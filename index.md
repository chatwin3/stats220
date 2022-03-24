library(magick)
dried_waterfall <- image_read("https://thumbs.dreamstime.com/z/%E5%9C%A8%E7%BB%BF%E5%B1%B1%E4%B8%AD%E5%B9%B2%E6%B6%B8%E7%9A%84%E7%80%91%E5%B8%83-%E5%B9%B2%E6%B6%B8%E7%9A%84%E7%80%91%E5%B8%83%EF%BC%8C%E5%9C%A8%E7%BB%BF%E5%B1%B1%E4%B8%AD%EF%BC%8C%E5%9C%A8%E5%BA%95%E9%83%A8%E7%9A%84%E7%9F%B3%E5%A4%B4-178560831.jpg") %>%
  image_scale(500)

bad_text <- image_blank(width = 500, 
                          height = 500, 
                          color = "#000000") %>%
  image_annotate(text = "bad",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

beautiful_waterfall <- image_read("https://p1-bk.byteimg.com/tos-cn-i-mlhdmxsy5m/9787acfddaa14a8b87d863285732ccd6~tplv-mlhdmxsy5m-q75:0:0.image") %>%
  image_scale(500)

good_text <- image_blank(width = 500, 
                       height = 500, 
                       color = "#000000") %>%
  image_annotate(text = "good",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

bad_vector <- c(dried_waterfall, bad_text)
top_row <- image_append(bad_vector)

bottom_row <- image_append(c(beautiful_waterfall, good_text))

meme <- c(top_row, bottom_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)

image_write(meme, "my_meme.png")

