# Stand-Up-Comedian
import flet as ft
import random

jokes = [
    "¿Qué hace un pez en la oficina? Nada. HAHAHA 😂",
    "¿Qué le dice el 1 al 10? Para ser como yo, tienes que ser sincero. BAHAHAH😆",
    "¿Cuál es la planta que da más miedo? El bambú. SO FUNNY🎋",
    "¿Cómo se llama el primo vegano de Bruce Lee? Broco Lee. BAHAHAH STOP🥦",
    "¿Qué hace una vaca pensando? Leche concentrada. SO FUNNYYYY LAUGHT🥛",
    "¿Por qué el plátano fue al hospital? Porque no se pelaba bien. 🍌",
    "Van dos ciegos y uno dice: 'Ojalá lloviera'. El otro responde: 'Ojalá yo también'. BRO HAHAHAH🕶️",
    "Doctor, doctor, tengo paperas. —Toma 2€ y ya tienes pa' plátanos. HAHAHA RIETEEEE🚑",
    "¿Por qué los diabéticos no pueden vengarse? Porque la venganza es dulce. HAHAAHAHAHAHA Q RISA🍪",
    "Si los ciempiés tienen 100 pies... ¿los piojos tienen 3,14 ojos? ESTE SI DA RISA HAHAHAH🪲"
]

def main(page: ft.Page):
    page.title = "Chistes Random"
    page.theme_mode = "light"
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
    page.vertical_alignment = ft.MainAxisAlignment.CENTER

    joke_text = ft.Text(value="", size=18, text_align="center")

    def close_sheet(e):
        sheet.open = False
        page.update()

    sheet = ft.BottomSheet(
        content=ft.Container(
            content=ft.Column(
                [
                    joke_text,
                    ft.ElevatedButton("dale aquí", on_click=close_sheet, icon=ft.icons.CLOSE)
                ],
                alignment="center",
                horizontal_alignment="center",
                spacing=20
            ),
            padding=20
        )
    )

    page.overlay.append(sheet)

    def show_joke(e):
        joke_text.value = random.choice(jokes)
        sheet.open = True
        page.update()

    joke_button = ft.ElevatedButton(
        text="haz clic para un chisteee!",
        on_click=show_joke,
    )

    page.add(
        ft.Column(
            [joke_button],
            alignment="center",
            horizontal_alignment="center",
            expand=True
        )
    )

ft.app(target=main)
