# mems-generate
mem.generate
from PIL import Image, ImageDraw, ImageFont

top_text = input("Введите верхний текст мема: ")
bottom_text = input("Введите нижний текст мема:")

print("Генератор мемов запущен!")

print(top_text, bottom_text)


print("Список картинок:")
print("1. Кот в ресторане")
print("2. Кот в очках")

image_number = input("Введи номер нужной картинки: ")



if image_number == "1" :
    image = "Кот в ресторане.png"
elif image_number == "2" :
    image = "Кот в очках.png"
print(image)

image = Image.open(f"./lesson 1/{image}")
width, height = image.size

draw = ImageDraw.Draw(image)

font = ImageFont.truetype("arial.ttf", size=70)

text = draw.textbbox((1300, 1300), top_text, font)
text_width = text[2]

draw.text((width - text_width / 2, 10), top_text, font=font, fill="black")

text = draw.textbbox((1300, 0), bottom_text, font)
text_width = text[2]
text_height = text[3]

draw.text((width - text_width / 2, height - text_height - 10), bottom_text, font=font, fill="black")

image.save("new_meme.jpg")
