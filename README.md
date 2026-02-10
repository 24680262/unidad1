# Programa de una Calculadora

> [!CAUTION]
> -Necesario crear un entorno virtual.
> 
> -Git Bash.
> 
> -Python 3.10 en adelante (puedes revisarlo con el comando "python --doctor" en Git Bash)

En este documento veremos el paso a paso de como realizar una calculadora que corra en Flet usando Python.

## Paso 1
Importamos Flet como un el paquete "ft" para que nos sea mas comodo llamarlo, ademas de ejecutar una segunda linea de codigo para ignorar errores molestos relacionados a la version de Flet.
```python
import flet as ft
import warnings
warnings.filterwarnings ("ignore", category= DeprecationWarning)
```
## Paso 2
Definimos en main en el cual vamos a trabajar todo nuestro codigo, y despues damos forma a nuestra ventana, para que se vea bien.
```python
def main(page: ft.Page):

    page.title ="Calculadora TAP" 
    page.window_width = 250 
    page.window_height = 400 
    page.padding = 20
```
## Paso 3
Definimos el como va a verse el texto que ingresemos a la calculadora.
```python
texto_visual = ft.Text("0", size=20)
```
## Paso 4
Nuestro Container en el cual se veran los numeros/simbolos que vayamos ingresando, para eso llamamos a nuestra variable "texto_visual", ademas de declarar sus medidas, color y su ubicacion.
```python
display = ft.Container(
        content=texto_visual,
        bgcolor=ft.Colors.BLACK12,
        border_radius=8,
        alignment=ft.alignment.Alignment(1, 0),
        padding=20,
        width=210, #Forzamos el ancho manualmente
        height=70,
    )
```
##  Paso 5
Despues programas el evento para que al clickear los numeros estos vayan aparenciendo, esto creando una variable que tenga el "e.control.data" que hace que se guarden los valores clickeados.
Ademas hacemos uso de un ciclo if para que en caso de presionar "C" se limpie la pantalla y volver a escribir otros numeros.
```python
def boton_click(e):
        valor_presionado= e.control.data

        if valor_presionado == "C":
            texto_visual.value = "0"
        else:
             if texto_visual.value == "0":
                    texto_visual.value = valor_presionado
             else:
                texto_visual.value += valor_presionado
        page.update()
```
## Paso 6
Creamos el Grid, el cual nos ayuda a ubicar de forma cuadriculadad los botones que vayamos creando.
```python
grid = ft.GridView(
        runs_count=4,
        spacing=10,
        run_spacing=10,
        width=210, # Ancho fijo igual al display
        height=200, # Alto fijo para que no crezca
        expand=False
    )
```
## Paso 7

```python
botones = [
        ("1", ft.Colors.PRIMARY),
        ("2", ft.Colors.SECONDARY),
        ("3", ft.Colors.TERTIARY),
        ("+", ft.Colors.AMBER),
        ("4", ft.Colors.PRIMARY),
        ("5", ft.Colors.SECONDARY),
        ("6", ft.Colors.TERTIARY),
        ("-", ft.Colors.ORANGE),
        ("7", ft.Colors.PRIMARY),
        ("8", ft.Colors.SECONDARY),
        ("9", ft.Colors.TERTIARY),
        ("*", ft.Colors.GREEN),
        ("0", ft.Colors.PRIMARY),
        ("C",ft.Colors.ERROR),
        ("/", ft.Colors.YELLOW),
        ("=", ft.Colors.BLUE)
    ]
```
