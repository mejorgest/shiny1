# shiny1

pip install shiny

from shiny import App, ui, render

## UI
app_ui = ui.page_fluid(
  ui.h3("Esto es una aplicación WEB."),
  ui.input_text(id = 'entrada', label = "Campo de texto:", value = 'Valor inicial'),
  ui.br(),
  ui.output_text("salida")
)

## servidor
def server(input, output, session):
  @output
  @render.text
  def salida():
    return("La salida es: " + input.entrada())

## Aplicación completa
app = App(app_ui, server)


from shiny import App, render, ui

## UI
app_ui = ui.page_fluid(
  
  ui.input_text(
    id = "texto", # Id de la entrada.
    label = "Campo de texto: ",  # Título de la entrada.
    value = "valor",  # Valor por defecto.
    width = "100%",  # Ancho de la entrada.
    placeholder = "Agregue el texto",  # Texto a mostrar cuando el campo esta vacío.
  ),
  
  ui.input_text_area(
    id = "text_area", # Id de la entrada.
    label = "Campo de area texto: ",  # Título de la entrada.
    value = "valor",  # Valor por defecto.
    width = "100%",  # Ancho de la entrada.
    placeholder = "Agregue el texto",  # Texto a mostrar cuando el campo esta vacío.
  ),
  
  ui.input_numeric(
    id = "numero", # Id de la entrada.
    label = "Campo numérico: ",  # Título de la entrada.
    value = 4,  # Valor por defecto.
    min = 0,  # Mínimo valor posible.
    max = 10,  # Máximo valor posible.
    step = 2,  # Intervalo de incremento o decremento.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_select(
    id = "seleccion", # Id de la entrada.
    label = "Campo de selección: ",  # Título de la entrada.
    choices = ["a", "b", "c", "d"],  # Opciones posibles.
    selected = "c",  # Opción seleccionada por defecto.
    multiple = False,  # Permite varias opciones si es True.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_slider(
    id = "slider", # Id de la entrada.
    label = "Campo de slider: ",  # Título de la entrada.
    min = 0,  # Mínimo valor posible.
    max = 10,  # Máximo valor posible.
    value = 4,  # Valor por defecto.
    step = 2,  # Intervalo de incremento o decremento.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_switch(
    id = "switch", # Id de la entrada.
    label = "Campo de switch: ",  # Título de la entrada.
    value = True,  # Valor por defecto.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_checkbox(
    id = "checkbox", # Id de la entrada.
    label = "Campo de checkbox: ",  # Título de la entrada.
    value = True,  # Valor por defecto.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_checkbox_group(
    id = "checkbox_group", # Id de la entrada.
    label = "Campo de checkbox_group: ",  # Título de la entrada.
    choices = ["a", "b", "c", "d"],  # Opciones posibles.
    selected = "c",  # Opción seleccionada por defecto.
    inline = True,  # Valor por defecto.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_radio_buttons(
    id = "radio_buttons", # Id de la entrada.
    label = "Campo de radio_buttons: ",  # Título de la entrada.
    choices = ["a", "b", "c", "d"],  # Opciones posibles.
    selected = "c",  # Opción seleccionada por defecto.
    inline = True,  # Valor por defecto.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_date(
    id = "date", # Id de la entrada.
    label = "Campo de date: ",  # Título de la entrada.
    value = "2023-01-01",  # Valor por defecto.
    min = "2022-01-01",  # Mínimo valor posible.
    max = "2024-01-01",  # Máximo valor posible.
    format = "yyyy-mm-dd", # Máximo valor posible.
    startview = "month", # Máximo valor posible.
    weekstart = 0, # Máximo valor posible.
    language = "es", # Máximo valor posible.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_date_range(
    id = "date_range", # Id de la entrada.
    label = "Campo de date_range: ",  # Título de la entrada.
    start = "2023-01-01",  # Valor por defecto.
    end = "2023-01-07",  # Valor por defecto.
    min = "2022-01-01",  # Mínimo valor posible.
    max = "2024-01-01",  # Máximo valor posible.
    format = "yyyy-mm-dd", # Máximo valor posible.
    startview = "month", # Máximo valor posible.
    weekstart = 0, # Máximo valor posible.
    language = "es", # Máximo valor posible.
    separator = " hasta ", # Máximo valor posible.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_file(
    id = "subida", # Id de la entrada.
    label = "Campo de subida: ",  # Título de la entrada.
    multiple = False,  # Título de la entrada.
    accept = [".csv", "application/pdf", "image/*"],  # Título de la entrada.
    width = "100%"  # Ancho de la entrada.
  ),
  
  ui.input_action_button(
    id = "boton", # Id de la entrada.
    label = "Boton",  # Título de la entrada.
    width = "100%",  # Ancho de la entrada.
  )
)

## servidor
def server(input, output, session):
  pass

## Aplicación completa
app = App(app_ui, server)


import pathlib
import pandas as pd
import matplotlib.pyplot as plt
from shiny import App, render, ui

ruta = pathlib.Path(__file__).parent

## UI
app_ui = ui.page_fluid(
  
  ui.h3("Grafico"),
  ui.output_plot(
    id = "grafico", # Id de la salida.
  ),
  ui.hr(),
  
  ui.h3("Tabla"),
  ui.output_table(
    id = "tabla", # Id de la salida.
  ),
  ui.hr(),
  
  ui.h3("Tabla Datos"),
  ui.output_data_frame(
    id = "tabladatos", # Id de la salida.
  ),
  ui.hr(),
  
  ui.h3("Texto"),
  ui.output_text(
    id = "texto", # Id de la salida.
  ),
  ui.hr(),
  
  ui.h3("Texto Código"),
  ui.output_text_verbatim(
    id = "textocodigo", # Id de la salida.
  ),
  ui.hr(),
  
  ui.h3("HTML"),
  ui.output_ui(
    id = "html", # Id de la salida.
  ),
  ui.hr()
)

## servidor
def server(input, output, session):
  
  iris = pd.read_csv(str(ruta) + "/www/data/iris.csv", sep = ";", decimal = ".")
  
  @output
  @render.plot
  def grafico():
    fig, ax = plt.subplots()
    ax.boxplot(iris.iloc[:, 0:4])
    return fig
  
  @output
  @render.table
  def tabla():
    return iris.head()
  
  @output
  @render.data_frame
  def tabladatos():
    return render.DataGrid(iris, height = "350px", width = "100%", filters = True)
  
  @output
  @render.text
  def texto():
    return iris.dtypes
  
  @output
  @render.text
  def textocodigo():
    return iris.dtypes
  
  @output
  @render.ui
  def html():
    return ui.input_checkbox(id = "checkbox", label = "Campo de checkbox: ", value = True, width = "100%")

## Aplicación completa
app = App(app_ui, server)

from shiny import App, render, ui

## UI
app_ui = ui.page_fluid(
  
  # h1 define el tamaño del texto.
  # Pueden ser h1, h2, h3, h4, h5 y h6.
  # Entre más grande el número más paqueña la letra.
  ui.h1("Título"),
  
  # Se pueden agregar atributos.
  # Para ello se debe agregar un diccionario
  # indicando el nombre del atributo y el valor
  ui.h2(
    {"style": "font-weight: bold;"},
    "Subtitulo"
  ),
  
  # Se pueden agregar varios atributos.
  ui.h3(
    {"id": "identificador", "style": "color: red;font-style: italic;"},
    "texto"
  ),
  
  # hr agrega una linea horizontal.
  ui.hr(),
  
  # div crea secciones.
  ui.div(
    {"style": "background-color: orange;"},
    ui.h3("Más texto"),
    
    # a crea hipervinculos.
    ui.a({"href": "https://promidat.website/"}, "PROMiDAT")
  ),
  
  ui.img({"src": "https://promidat.website/wp-content/uploads/2021/09/cropped-cropped-L003-Logo-Promidat-Horizontal-1.jpg"})
)

## servidor
def server(input, output, session):
  pass

## Aplicación completa
app = App(app_ui, server)


from shiny import App, render, ui

app_ui = ui.page_fluid(
  ui.input_text("texto", "Digite el texto: ", placeholder="Enter text"),
  ui.input_select("seleccion", "Seleccione una opción: ", choices = ["a", "b", "c"]),
  ui.input_checkbox("checkbox", "Seleccione la opción: ", True),
  ui.hr(),
  ui.h3("Salida 1"),
  ui.output_text_verbatim("salida1"),
  ui.hr(),
  ui.h3("Salida 2"),
  ui.output_text_verbatim("salida2")
)

def server(input, output, session):
  
  # La salida se debe llamar igual al id que se indico en el UI.
  @output
  @render.text
  def salida1():
    # Para que la salida se modifique solo hay que invocar
    # la o las entradas deseadas.
    texto = input.texto()
    checkbox = str(input.checkbox())
    res = "Texto: " + texto + ", Opcion: " + checkbox
    return res
  
  @output
  @render.text
  def salida2():
    texto = input.texto()
    seleccion = str(input.seleccion())
    res = "Texto: " + texto + ", Opcion: " + seleccion
    return res


app = App(app_ui, server)


from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.input_text("texto", "Digite el texto: ", placeholder="Enter text"),
  ui.input_select("seleccion", "Seleccione una opción: ", choices = ["a", "b", "c"]),
  ui.input_checkbox("checkbox", "Seleccione la opción: ", True),
  ui.hr(),
  ui.input_action_button("boton", "Ejecutar"),
  ui.hr(),
  ui.h3("Salida 1"),
  ui.output_text_verbatim("salida1"),
  ui.hr(),
  ui.h3("Salida 2"),
  ui.output_text_verbatim("salida2")
)

def server(input, output, session):
  
  @output
  @render.text
  def salida1():
    input.boton()
    # Todo lo que se encuentre dentro de la función reactive.isolate
    # no va a reactivar la salida.
    with reactive.isolate():
      texto = input.texto()
      checkbox = str(input.checkbox())
    res = "Texto: " + texto + ", Opcion: " + checkbox
    return res
  
  @output
  @render.text
  def salida2():
    texto = input.texto()
    seleccion = str(input.seleccion())
    res = "Texto: " + texto + ", Opcion: " + seleccion
    return res


app = App(app_ui, server)


from datetime import datetime
from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.h3("Salida"),
  ui.output_ui("salida")
)

def server(input, output, session):
  
  # Para definir una variable reactiva utilizamos la función reactive.Value.
  # Se puede almacenar cualquier tipo de dato, incluso un data.frame.
  fecha = reactive.Value(datetime.now())
  
  # Para definir una función reactiva utilizamos el decorador reactive.Effect.
  # El nombre de la función no es relevante por lo que puede ser cualquiera.
  # Para activar la función al igual que con las salidas se puede usar
  # cualquier elemento reactivo como una variable reactiva o una entrada.
  @reactive.Effect
  def _():
    # La siguiente función reactiva el evento cada segundo.
    reactive.invalidate_later(1)
    
    # Para modificar el valor de una variable reactiva debemos
    # invocar el método set.
    fecha.set(datetime.now())
  
  @output
  @render.text
  def salida():
    # Para obtener el valor de una variable reactiva debemos
    # invocar el método get.
    valor = fecha.get()
    valor = valor.strftime("%d/%m/%Y %H:%M:%S")
    res = ui.h2(valor)
    return res

app = App(app_ui, server)


from shiny import App, render, ui, reactive
# page_fluid crea una página básica.
app_ui = ui.page_fluid(
  # Contenido
  "Contenido",
  
  # Titulo
  title = "Aplicación"
)

def server(input, output, session):
  pass

app = App(app_ui, server)


from shiny import App, render, ui, reactive
# page_navbar crea una página con encabezado.
# El encabezado puede contener tabs de navegación.
app_ui = ui.page_navbar(
  # Cada nav es un tab de navegación.
  ui.nav_panel(
    # Titulo
    "TAB 1",
    
    # Contenido
    "Contenido 1"
  ),
  
  ui.nav_panel(
    # Titulo
    "TAB 2",
    
    # Contenido
    "Contenido 2"
  ),
  
  # Titulo
  title = "Aplicación",
  
  # Color del encabezado
  bg = "steelblue"
  
)

def server(input, output, session):
  pass

app = App(app_ui, server)


from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  # layout_sidebar define un diseño con una barra lateral.
  ui.layout_sidebar(
    # sidebar define el contenido de la barra lateral.
    ui.sidebar(
      # Contenido
      "Contenido barra lateral",
      
      # Ancho de la barra lateral.
      width = "500px",
      
      # Posición (puede ser left o right)
      position = "right",
      
      # Color de la barra lateral.
      bg = "steelblue"
    ),
    
    # Contenido principal.
    "Contenido principal",
    
    # Color principal
    bg = "white"
  )
)

def server(input, output, session):
  pass

app = App(app_ui, server)
from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.card(
    # Encabezado carta
    ui.card_header("Encabezado"),
    
    # Contenido
    "Contenido carta",
    
    # Pie carta
    ui.card_footer("Pie")
  ),
  
  title = "Cartas"
)

def server(input, output, session):
  pass

app = App(app_ui, server)

from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.navset_card_tab(
    # Cada nav es un tab de navegación.
    ui.nav_panel(
      # Titulo
      "TAB 1",
      # Contenido
      "Contenido 1"
    ),
    
    ui.nav_panel(
      # Titulo
      "TAB 2",
      
      # Contenido
      "Contenido 2"
    )
  ),
  
  title = "Cartas"
)

def server(input, output, session):
  pass

app = App(app_ui, server)


from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.input_action_button("mostrar", "Mostrar"),
  
  # Titulo
  title = "Notificaciones"
)

def server(input, output, session):
  @reactive.Effect
  @reactive.event(input.mostrar)
  def _():
    # Mostrar notificación
    ui.notification_show(
      "Mensaje", # Mensaje
      duration = 10 # Duración en pantalla en segundos
    )

app = App(app_ui, server)
from shiny import App, render, ui, reactive

app_ui = ui.page_fluid(
  ui.input_action_button("mostrar", "Mostrar"),
  
  # Titulo
  title = "Notificaciones"
)

def server(input, output, session):
  @reactive.Effect
  @reactive.event(input.mostrar)
  def _():
    # Mostrar notificación
    m = ui.modal(
      "Contenido", # Contenido
      title = "Título", # Título
      easy_close = True # Fácil de cerrar
    )
    ui.modal_show(m)

app = App(app_ui, server)



import numpy as np
import pandas as pd
from math import pi
import matplotlib.pyplot as plt
from shiny import App, render, ui, reactive
from scipy.cluster.hierarchy import fcluster, linkage

app_ui = ui.page_navbar(
  ui.nav_panel(
    "Cargar Datos",
    ui.layout_sidebar(
      ui.sidebar(
        ui.input_file(
          id = "archivo",
          label = "Subir archivo: ",
          multiple = False,
          accept = [".csv"],
          width = "100%"
        ),
        ui.input_radio_buttons(
          id = "sep",
          label = "Seleccione el separador de datos: ",
          choices = [";", ","],
          inline = True,
          width = "100%"
        ),
        ui.input_radio_buttons(
          id = "dec",
          label = "Seleccione el separador de decimales: ",
          choices = [",", "."],
          inline = True,
          width = "100%"
        ),
        ui.input_switch(
          id = "rownames",
          label = "¿Nombres de fila?",
          value = True,
          width = "100%"
        ),
        ui.input_action_button("cargar", "Cargar Datos")
      ),
      ui.output_data_frame(id = "tabladatos")
    )
  ),
  ui.nav_panel(
    "Dispersión",
    ui.card(
      ui.card_header("Opciones"),
      ui.row(
        ui.column(6, ui.input_select("varx", "Seleccione una variable: ", [])),
        ui.column(6, ui.input_select("vary", "Seleccione una variable: ", []))
      )
    ),
    ui.output_plot("dispersion")
  ),
  ui.nav_panel(
    "Clusterización",
    ui.row(
      ui.column(
        4,
        ui.card(
          ui.card_header("Opciones"),
          ui.input_slider("nclusters", "Indique la cantidad de clusters: ", 2, 10, 2),
          ui.input_select("agrupacion", "Seleccione método de agrupación: ", ["single", "complete", "average", "ward"]),
          ui.input_select("distancia", "Seleccione método de distancia: ", ["euclidean", "minkowski", "canberra"]),
          ui.hr(),
          ui.input_action_button("generar", "Generar Modelo"),
        )
      ),
      ui.column(
        8, 
        ui.card(ui.card_header("Clusters"), ui.output_data_frame(id = "tablaclusters")),
        ui.card(ui.card_header("Gráfico Radar"), ui.output_plot("radar"))
      )
    )
  ),
  title = "Aplicación",
  bg = "steelblue"
)

def server(input, output, session):
  datos = reactive.Value(None)
  clusters = reactive.Value(None)
  
  def centroide(datos, clusters):
    real = pd.DataFrame()
    for x in np.unique(clusters):
      real[x] = datos.iloc[clusters == x, :].mean()
    porc = real.copy()
    for i in range(porc.shape[0]):
      aux = porc.iloc[i, :] - min(porc.iloc[i, :])
      porc.iloc[i, :] = aux / max(aux)
    return {"real" : real, "porc" : porc}
  
  @reactive.Effect
  def _():
    input.cargar()
    try:
      with reactive.isolate():
        ruta = input.archivo()[0]["datapath"] # name: Nombre del archivo
        sep = input.sep()
        dec = input.dec()
        rownames = input.rownames()
        if rownames:
          rownames = 0
      
      aux = pd.read_csv(ruta, sep = sep, decimal = dec, index_col = rownames)
      datos.set(aux)
      ui.update_select("varx", choices = aux.columns.tolist())
      ui.update_select("vary", choices = aux.columns.tolist())
    except Exception as e:
      ui.notification_show(str(e), duration=5)
      datos.set(None)
  
  @output
  @render.data_frame
  def tabladatos():
    df = datos.get()
    if df is None:
      return None
    return render.DataGrid(df, height = "350px", width = "100%", filters = True)
  
  @output
  @render.plot
  def dispersion():
    df = datos.get()
    varx = input.varx()
    vary = input.vary()
    if df is None:
      return None
    try:
      fig, ax = plt.subplots()
      ax.scatter(df.loc[:, varx], df.loc[:, vary])
      return fig
    except Exception as e:
      ui.notification_show(str(e), duration=5)
      return None
  
  @reactive.Effect
  def _():
    input.generar()
    with reactive.isolate():
      df = datos.get()
      nclusters = input.nclusters()
      agrupacion = input.agrupacion()
      distancia = input.distancia()
    
    if df is None:
      clusters.set(None)
    else:
      df = df.copy()
      df = pd.get_dummies(df)
      grupos = fcluster(
        linkage(df, method = agrupacion, metric = distancia),
        nclusters, criterion = 'maxclust')
      grupos = grupos - 1
      clusters.set(grupos)
  
  @output
  @render.data_frame
  def tablaclusters():
    cl = clusters.get()
    
    with reactive.isolate():
      df = datos.get()
    
    if df is None or cl is None:
      return None
    df = df.copy()
    df['Clusters'] = cl
    return render.DataGrid(df, height = "350px", width = "100%", filters = True)
  
  @output
  @render.plot
  def radar():
    cl = clusters.get()
    
    with reactive.isolate():
      df = datos.get()
    
    if df is None or cl is None:
      return None
    
    df = df.copy()
    df = pd.get_dummies(df)
    centros = centroide(df, cl)
    etq = centros["porc"].index.values
    angulos = [n / float(len(etq)) * 2 * pi for n in range(len(etq))]
    angulos += angulos[:1]
    
    fig, ax = plt.subplots()
    ax = plt.subplot(111, polar = True)
    ax.set_theta_offset(pi / 2)
    ax.set_theta_direction(-1)
    
    plt.xticks(angulos[:-1], etq)
    ax.set_rlabel_position(0)
    plt.yticks(
      [10, 20, 30, 40, 50, 60, 70, 80, 90, 100],
      ["10%", "20%", "30%", "40%", "50%", "60%", "70%", "80%", "90%", "100%"], 
      color = "grey", size = 8)
    plt.ylim(-10, 100)
    for x in centros["porc"].columns:
      valores = round(centros["porc"].loc[:, x] * 100, 2).tolist()
      valores += valores[:1]
      ax.plot(angulos, valores, linewidth = 1, linestyle = 'solid', label = x)
      ax.fill(angulos, valores, alpha = 0.3)
    
    plt.legend(loc='upper right', bbox_to_anchor = (0.1,  0.1))
    return fig

app = App(app_ui, server)












