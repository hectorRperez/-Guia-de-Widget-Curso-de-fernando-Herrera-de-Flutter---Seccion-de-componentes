## 072 Modelo de creación de un Widget Card

Codigo de ejemplo

```

Widget cardTipo1() {
    return Card(
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10.5)),
      elevation: 10.5,
      child: Column(
        children: [
          ListTile(
           title: Text('Hola Mundo'),
            subtitle: Text('Aquí va un texto cualquiera de ejemplo,Aquí va un texto cualquiera de ejemplo'),
            leading: Icon(Icons.photo_album, color: Colors.teal,),
          ),
          Row(
            mainAxisAlignment: MainAxisAlignment.end,
            children: [
              FlatButton(child: Text('Cancelar'),onPressed: (){},),
              FlatButton(child: Text('Ok'),onPressed: (){}),
            ],
          ),
        ],
      ),
    );
  }

```

## 073 Modelo de creación de un Widget Card utilizando un FadeInImage

Codigo de ejemplo

```

Widget cardTipo2() {
    return Card(
      elevation: 10.5,
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20.5)),
      clipBehavior: Clip.antiAlias,
      shadowColor: Colors.black87,
      child: Column(
        children: [
          FadeInImage(
            image: NetworkImage('https://images3.alphacoders.com/997/997848.jpg'),
            placeholder: AssetImage('assets/jar-loading.gif'),
            height: 250.0,
            fit: BoxFit.cover,
          ),
          Container(
            padding: EdgeInsets.all(10.0),
            child: Text('Esto es un texto',style: TextStyle(fontSize: 20.5),),
          ),
        ],
      ),
    );
  }

```

## 076 Crear un Widget Alert

~~~
void _mostrarAlerta(BuildContext context) {
    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20.5)),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              ListTile(
                title: Text('Titulo de la tarjeta', style: TextStyle(fontSize: 20.5),),
                subtitle: Text('Aquí va otra información adicional'),
              ),
              FlutterLogo(size: 80.5,),
            ],
          ),
          actions: [
            FlatButton(child: Text('Cancelar'),textColor: Colors.teal,onPressed: ()=> Navigator.pop(context),),
            FlatButton(child: Text('Ok'),textColor: Colors.teal,onPressed: ()=> Navigator.pop(context)),
          ],
        );
      },
    );
  }
~~~

## 076 Crear un Widget Circle Avatar

~~~
class AvatarPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Avatar Page'),
        actions: [
          Container(
            margin: EdgeInsets.all(5.5),
            child: CircleAvatar(
              backgroundImage: NetworkImage('https://img3.wikia.nocookie.net/__cb20110623004448/theclonewiki/images/e/e3/Gree.jpg'),
              radius: 25.5,
            ),
          ),
        ],
      ),
      body: Center(
        child: FadeInImage(
          image: NetworkImage('https://img3.wikia.nocookie.net/__cb20110623004448/theclonewiki/images/e/e3/Gree.jpg'),
          placeholder: AssetImage('assets/jar-loading.gif'),
        ),
      ),
    );
  }
}
~~~

## 078 Modelo de creación de un AnimatedContainer

~~~
import 'package:flutter/material.dart';
import 'dart:math' show Random;

class AnimatedContainerPage extends StatefulWidget {
  @override
  _AnimatedContainerPageState createState() => _AnimatedContainerPageState();
}

class _AnimatedContainerPageState extends State<AnimatedContainerPage> {
  double _height = 50.0;
  double _width = 50.0;
  Color _color = Colors.pink;
  BorderRadiusGeometry _border = new BorderRadius.circular(10.5);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Animated Container'),
      ),
      body: Center(
        child: AnimatedContainer(
          duration: Duration(seconds: 1),
          curve: Curves.fastOutSlowIn,
          height: _height,
          width: _width,
          decoration: BoxDecoration(
            borderRadius: _border,
            color: _color,
          ),
        ),
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.play_arrow),
        backgroundColor: Colors.teal,
        onPressed: () => animar(),
      ),
    );
  }

  void animar() {
    Random _random = new Random();
    setState(() {
      _width = _random.nextInt(300).toDouble();
      _height = _random.nextInt(300).toDouble();
      _color = Color.fromRGBO(
        _random.nextInt(256),
        _random.nextInt(256),
        _random.nextInt(256),
        1,
      );
      _border = BorderRadius.circular(_random.nextInt(100).toDouble());
    });
  }
}
~~~

## 079 Modelo de creación de un Inputs

Propiedades de un TextField 

- autofocus -> Coloca el cursor automatico en TextField
- textCapitalization establece como mostrar las palabras en el TextField

  Parametros 
  - TextCapitalization.sentences,
  - TextCapitalization.characters
  - TextCapitalization.none (viene por defecto)
  - TextCapitalization.words 

- decoration -> Propiedades para decorar aún más la caja de texto
  
  Parametros
  - counter -> Recibe cualquer Widget
  - hintText -> Recibe un String (Un texto que se muestra dentro de la caja de texto)    
  - labelText -> Un label de ayuda, recibe un String
  - helperText -> Texto de ayuda que va abajo de la caja de texto, recibe un String
  - suffixIcon -> Icon que va dentro de la caja de texto
  - icon -> Icon que va fuera de la caja de texto
  - border -> Muestra un border al rededos de la caja de texto
    Propiedades
    - UnderlineInputBorder
    - OutlineInputBorder


~~~
Widget _crearPersona() {
    return TextField(
      // autofocus: true,
      textCapitalization: TextCapitalization.sentences,
      decoration: InputDecoration(
        counter: Text('Letras 0'),
        hintText: 'Nombre de la persona',
        labelText: 'Nombre',
        helperText: 'Solo el nombre',
        suffixIcon: Icon(Icons.accessibility),
        icon: Icon(Icons.account_circle),
        border: OutlineInputBorder(borderRadius: BorderRadius.circular(20.0)),
      ),
      onChanged: (valor) {
        setState(() {
          _nombre = valor;
        });
      },
    );
  }
~~~

## 080 Modelo de creación de un Inputs de Email

~~~
Widget _crearEmail() {
    return TextField(
      keyboardType: TextInputType.emailAddress,
      decoration: InputDecoration(
        hintText: 'example@gmail.com',
        labelText: 'Email',
        helperText: 'correo electronico',
        suffixIcon: Icon(Icons.lock),
        icon: Icon(Icons.lock_open),
        border: OutlineInputBorder(borderRadius: BorderRadius.circular(20.0)),
      ),
      onChanged: (valor) {
        setState(() {
          _mail = valor;
        });
      },
    );
  }
~~~

## 080 Modelo de creación de un Inputs de Password

~~~

Widget _crearPassword() {
    return TextField(
      obscureText: true,
      decoration: InputDecoration(
        hintText: '**********',
        labelText: 'Password',
        helperText: 'Password',
        suffixIcon: Icon(Icons.lock),
        icon: Icon(Icons.lock_open),
        border: OutlineInputBorder(borderRadius: BorderRadius.circular(20.0)),
      ),
      onChanged: (valor) {
        setState(() {
          _mail = valor;
        });
      },
    );
  }

~~~

081 Modelo de creación de un Inputs de Password

## 081 Modelo de creación de un Calendario

Trabajar con Datepicker

Codigo modelo para trabajar con Widget para atrapar una fecha

- FocusScope.of(context).requestFocus(new FocusNode()); -> No permite seleccionar el TextField
- enableInteractiveSelection: false, -> No permite ni copiar ni pegar el texto del TextField
- La propiedad controller permite asignar una variable al widget mendiante esta propiedad

Modelo basico de widget
~~~
Widget _crearFecha() {
    return TextField(
      controller: inputFieldDateControlle,
      enableInteractiveSelection: false,
      decoration: InputDecoration(
        labelText: 'Fecha de nacimiento',
        suffixIcon: Icon(Icons.calendar_today),
        icon: Icon(Icons.perm_contact_calendar),
        border: OutlineInputBorder(
          borderRadius: BorderRadius.circular(20.5),
        ),
      ),
      onTap: (){
        FocusScope.of(context).requestFocus(new FocusNode());
        _selectDate(context);
      },
    );
  }
~~~

Modelo de creación de una funcion que lanza un modal de calendario

- forma de declara una variable de tipo TextEditingController

~~~
TextEditingController inputFieldDateControlle = new TextEditingController();
~~~

Ya se puede asignar valor con esta variable a un widget con propiedad *controller*

- showDatePicker regresa un future por eso se trabaja con async - await
- inputFieldDateControlle.text = fecha; -> Forma de asigar un valor a una variable de tipo TextEditingController

~~~
void _selectDate(BuildContext context) async{
    DateTime datePicket = await showDatePicker(
      context: context, 
      initialDate:  new DateTime.now(), 
      firstDate: new DateTime(2018), 
      lastDate: new DateTime(2022),
      );
      
      if (datePicket!=null){
        final fecha = datePicket.toString();
        inputFieldDateControlle.text = fecha;
      }
  }
~~~

## 083 Modelo de creación de Dropdown y DropdownMenuItem

Creación de un Widegt DropdownButton

La implementación es: 

  - value: Es el valor que se colocará en el DropdownButton
  - items: Son una lista de objetos que se monstraran en el DropdownButton
  - onChaged: Se implementará a fuerza en el DropdownButton

  Forma de implementarlo 

  ~~~
  List<DropdownMenuItem<String>> getOpcionesDropdown() {
    List<DropdownMenuItem<String>> _lista = new List();

    _poderes.forEach((element) {
      _lista.add(DropdownMenuItem(
        child: Text(element),
        value: element,
      ));
    });

    return _lista;
  }
  ~~~

  Nota: 
    El metodo getOpcionesDropdown se encarga de agregar los valores al DropdownButton. El metodo devuelve una Lista que almacena elementos de tipo String.

    - El metodo forEach se encarga de asignar los valores al DropdownMenuItem
      - child: Donde irá cada elemento de la lista.
      - value: Almacena el tipo de la lista, se puede pasar el elemento que se pasa al forEach

  ~~~
  Widget crearDropDown() {
    return Row(
      children: [
        Icon(Icons.select_all),
        Expanded(
          child: SizedBox(),
        ),
        DropdownButton(
          value: opcionSeleccionada,
          items: getOpcionesDropdown(),
          onChanged: (valor) {
            setState(() { 
              opcionSeleccionada = valor;
            });
          },
        ),
      ],
    );
  }
  ~~~

  Nota:
    value: Se almacena el valor que se mostrará en pantalla
    items: El value del DropdownButton alamcena una objeto que debe ser de tipo DropdownMenuItem que es lo que devuelve el getOpcionesDropdownmetodo. 
  
## 084 Modelo de creación de un Sliders

~~~
Widget _crearSlider() {
    return Slider(
      label: 'Tamaño de la imagen',
      activeColor: Colors.red,
      value: _valor,
      min: 60.0,
      max: 300.0,
      onChanged: (valor){ 
        setState(() {
          _valor = valor;
        });
      },

    );
  }
~~~

value: Será el valor que tendrá el elemento
min: tamaño minimo del elemento que se va a mostrar
max: tamaño maximo del elemento

## 085 Modelo de creación de un Checkbox y Switches

### Codigo basico para la creación de un checkbox
~~~
Widget _crearCheckBox() {
    return Checkbox(
      onChanged: (valor){
        setState(() {
          _checkBoxValue = valor;
        });
      },
      value: _checkBoxValue,
    );
  }
}
~~~

value: Es el valor que tendrá el elemento

### Codigo base para un checkBoxListTile
~~~
Widget _crearCheckBox() {
    return CheckboxListTile(
      title: Text('Bloquear imagen'),
      onChanged: (valor){
        setState(() {
          _checkBoxValue = valor;
        });
      },
      value: _checkBoxValue,
    );
  }
~~~

### Codigo base para crear un SwitchListTile

~~~
Widget _crearSitches() {
    return SwitchListTile(
      title: Text('Bloquear imagen'),
      onChanged: (valor){
        setState(() {
          _checkBoxValue = valor;
        });
      },
      value: _checkBoxValue,
    );
  }
~~~

## 086 Modelo de creación de un ListView Builder

Codigo base para un listView.Builder

~~~
 Widget _crearLista() {
    return ListView.builder(
      itemCount: 20,
      itemBuilder: (BuildContext context, int index){
        return FadeInImage(
          image: NetworkImage('https://picsum.photos/id/$index/500/300'),
          placeholder: AssetImage('assets/jar-loading.gif'),
          fit: BoxFit.cover,
          width: 500.0,
          height: 300.0,
        );
      },
    );
  }
~~~

Nota:
  - itemCount: Es un numero entero que se le pasa al ListView
  - itemBuilder: Donde salga la palabra builder se refiere a algo que se va a dibujar en pantalla
    - (BuildContext context, int index)
    - El context: Es el context de la aplicación
    - index: El index es el indice que se le asigna a cada elemento que se va a dibujar en pantalla


## 087 Modelo de creación de un InfiniteScroll


Codigo basico para la creación de una lista infinita
~~~
import 'package:flutter/material.dart';

class ListPage extends StatefulWidget {
  @override
  _ListPageState createState() => _ListPageState();
}

class _ListPageState extends State<ListPage> {

  <!-- Paso 3 -->
  <!-- Se crea un obejot de tipo ScrollController-->
  <!-- Sirve para manipular el estado de un Scroll -->
  ScrollController scrollController = new ScrollController();
  
  
  List <int> _listaNumeros = new List();
  int _contadorImage = 0;

  <!-- Paso 2 -->
  <!-- Este metodo se llama justo cuando el Widget se esta creando -->
  <!-- El metodo cargar10 se llama justo en este metodo para poder carga -->
  <!-- 10 imagenes al ListView.Builder -->
  @override
  void initState() {
    super.initState();
    _cargar10();

    <!-- Paso 5 -->
    <!-- Se agrega un Listener para poder escuchar cada cosa que el -->
    <!-- scroll realice -->
    <!-- Este metodo se va a disparar cada vez que se mueva el scroll -->
    scrollController.addListener(() { 

      <!-- Paso 6 -->
      <!-- Esta condicion evalua que el scroll llegue hasta el final de la  -->
      <!-- pantalla -->
      <!-- Cuando se llegue al final de la pantalla se cargan 10 imagenes más -->
      if (scrollController.position.pixels == scrollController.position.maxScrollExtent){
        _cargar10();
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Listas y scrolls'),
      ),
      body: _crearLista(),
    );
  }

  Widget _crearLista() {
    return ListView.builder(
      itemCount: _listaNumeros.length,

      <!-- Paso 4 -->
      <!-- El objeto de tipo scrollController se le asigna al ListView.Builder-->
      <!-- Para poder saber el estado del scroll -->
      controller: scrollController,
      itemBuilder:(BuildContext context, int index) {
        return FadeInImage(
          image: NetworkImage("https://picsum.photos/id/$index/500/300"),
          placeholder: AssetImage('assets/jar-loading.gif'),
          fit: BoxFit.cover,
          width: 500,
          height: 300,
        );
      },
      );
  }

  <!-- Paso 1 -->
  <!-- Metodo que se crea para cargar 10 imagenes más  -->
  void _cargar10(){
    for (var i = 0; i < 10; i++) {
      _contadorImage++; 
      <!-- Lista que va agregando numeros -->
      _listaNumeros.add(_contadorImage);
    }
    <!-- Se redibuja el widget -->
    setState(() {});
  }
}
~~~


## 088 Modelo de creación de un InfiniteScroll con Futures y retrasos de cargas

### Codigo de ejemplo para crear un retraso de carga

~~~

<!-- Paso 9 -->
<!-- Una bandera que nos indique que se esta pidiendo datos -->
<!-- _isLoading se cambiará cada vez que se llame el metodo _fetchData() -->
bool _isLoading = false; 

@override
  void initState() {
    super.initState();
    _cargar10();

    scrollController.addListener(() { 
      if (scrollController.position.pixels == scrollController.position.maxScrollExtent){
        
        <!-- Paso 7 -->
        <!-- Metodo que se crea para simular una petición HTTP a un servidor web -->
        _fetchData();
      }
    });
  }

  <!-- Paso 8  -->
  <!-- Se implementa el metodo para simular una petición con un retraso -->
  <!-- Devuelve un Future -->
  Future _fetchData() async{

    <!-- Paso 10 -->
    <!-- Para redibujar el Widget en pantalla -->
    _isLoading = true;
    setState(() {});

    <!-- Paso 11 para implementar un retraso en la peticion -->
    return new Timer(Duration(seconds: 5), respuestaHTTP);
  }

  <!-- Paso 12 -->
  <!-- Se implementa la simulación de carga HTTP -->
  void respuestaHTTP() {

    <!-- Paso 13 -->
    <!-- La variable _isLoading cambia porque ya se simulo la peticion HTTP -->
    _isLoading = false;

    <!-- Paso 14 se llama el metodo para cargar 10 imagenes más al ListView -->
    _cargar10();
  }

~~~

- El metodo *_fetchData()* es el que se encarga de crear un retraso en la carga de los datos

- El metodo retorna en new Timer que se encarga de ejecutar una función luego de un tiempo determinado

- *_isLoading* se encarga de decirnos si estan cargando los datos o no

### Borrar de memoria los scrollsCotrollers que se van creando

~~~
<!-- Paso 15  -->
<!-- Se debe destruir los controllers creados -->
<!-- El metodo dispose se ejecuta justo antes de eliminar una ruta de la pantalla -->
@override
  void dispose() {
    super.dispose();
    scrollController.dispose();
  }

~~~

- El metodo dispose() se dispara justo cuando la ruta en Flutter se cierra. El scrollController se elimina de memoria

### Crear un modelo de Loading usando CircularProgressIndicator

<!-- Paso 16 -->
<!-- Implementar un Stack-->

~~~
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Lista y Scroll'),
      ),
      <!-- Se apila todo con el Widget Stack -->
      body: Stack(
        children: [
          _crearLista(),
          <!-- Paso 17 se crea el metodo para diseñar en pantalla un loading -->
          _crearLoading()
        ],
      ),
    );
  }
~~~


<!-- Paso 17 -->
<!-- Se implementa el metodo que va a devolver el Widget -->
<!-- Se utiliza una condición para saber si se esta pidiendo datos o no -->
~~~
Widget _crearLoading() {
    if(_isLoading){
      return Column(
        mainAxisAlignment: MainAxisAlignment.end,
        children: [
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              CircularProgressIndicator(),
              SizedBox(height: 70.5,),
            ],
          ),
        ],
      );
    }else {
      return Container();
    }
  }
~~~


### Hacer que el scroll de la pantalla se deslice para mostrar más información
<!-- Paso 18 -->
<!-- Se modifica el metodo respuestaHTTP para mostrar la informació que ya cargo -->
<!-- Gracias al objeto scrollController se puede manipular el scroll que se mira en pantalla  -->
~~~
void respuestaHTTP() {
    _isLoading = false;
    _cargar10();
    scrollController.animateTo(
      scrollController.position.pixels + 100,
      curve: Curves.elasticIn,
      duration: Duration(milliseconds: 250),
    );
  }
~~~

## 089 Desarrollar un Pull to refresh

~~~
<!-- Modelo para crear un Pull request -->
Widget _crearLista() {
    return RefreshIndicator(
      <!-- la propiedad onRefresh-->
      <!-- Recibe un Future -->
      onRefresh: obtenerPagina1,
      child: ListView.builder(
        controller: _scrollController,
        itemCount: _listaNumero.length,
        itemBuilder: (BuildContext context, int index) {
          final imagen = _listaNumero[index];
          return FadeInImage(
            image: NetworkImage('https://picsum.photos/id/$imagen/500/300'),
            placeholder: AssetImage('assets/jar-loading.gif'),
            fit: BoxFit.cover,
            fadeInDuration: Duration(seconds: 2),
            height: 300,
            width: 500,
          );
        },
      ),
    );
  }
~~~

<!-- Modelo de creación de un metodo para crear un pull request -->
~~~
Future <Null> obtenerPagina1() async{

  final duration = new Duration(seconds: 10);
  new Timer(duration, (){
    _listaNumero.clear();
    _contador++;
    _cargar10();
  }); 
  return Future.delayed(duration);
}  
~~~
