<!--hide-->
# Clon de Meetup con API de contexto
<!--endhide-->

Tecnologías: HTML, CSS, JS, React, React Router and React Context API.

![Meetup.com Clone](https://github.com/breatheco-de/exercise-meetup-clone-react/blob/master/preview.png?raw=true)

👆 Este ejemplo esta optimizado para grupos de dos o máximo tres estudiantes.

¡Hola! Es hora de empezar a hacer aplicaciones frontales profesionales. Esta vez
Crearemos una pequeña aplicación de Meetup.com que permita a los usuarios navegar y confirmar eventos, muy similar a cómo funciona Meetup.com.

📹[Video completo de como debe funcionar la aplicacion aqui.](https://github.com/breatheco-de/exercise-meetup-clone-react/blob/master/preview.webm?raw=true)

- **Event**'s  son la entidad central en el sistema, la vista principal (Home) tendrá una lista de **Event**'s organizado por fechas.
- Cada **Event** esta vinculado _a single **Meetup**_.
- Un **Meetup** puede ser vinculado _uno a muchos_ **Event**s (one to many).


## Este proyecto está destinado a realizarse en dos fases.

1. Primero queremos enfocarnos en las imágenes, asegurarnos de que el front HTML/CSS y los componentes estén funcionando correctamente.
2. En segundo lugar, debemos implementar las llamadas fetch al backend y volver "dinámica" la aplicación con data real obtenida de la base de datos.

### Fase 1: Crea las vistas, luego vincúlalas con React Router en su componente de diseño.

Cada grupo debe crear las vistas: 
- Home (Lista de Eventos)
- Detalle del Event
- Detalle del Meetup

Usa contenido/data ficticia inicialmente, lo importante es que se vea bien.

En Meetup.com, Meetups son los grupos u organizaciones anfitrionas de los eventos. 

##### Cada Meetup debe tener:
- Título
- Descripción


En contraste, los eventos son los eventos específicos que el grupo está organizando durante el mes. 

##### Cada Evento debe tener:
- Título
- Descripción
- Fecha
- Hora
- Meetup


Nota: Piensa en DRY (Don't repeat yourself) y declara solo ***un*** componente y usa ```props``` para manejar una estructura similar pero contenido diferente.

RECUERDA: Las etiquetas `<a>` provocarán un redireccionamiento, que no deseas en React. En lugar de etiquetas `<a>` Asegúrate de usar el componente `<Link>` de React Router para implementar la navegación entre vistas.

```jsx

<Link to="/event">
	Title of event
</Link>
```


### Fase 2: dinamizar la aplicación implementando React Context.

***Utiliza el store para rellenar el contenido ficticio *** dentro de las vistas/componentes. Se puede acceder al store utilizando el ```Context.Consumer```

##### Referencia: Usando el Context

The `store` structure (```/store/store.js```):

Algunos contenidos ficticios.

```javascript
store = {
    events:[
        {
            ID: 36,
            post_content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec libero consectetur risus vehicula interdum eu at elit. Proin a commodo erat, eu molestie ipsum. Aliquam tristique nunc a est tristique, et convallis risus ullamcorper. Fusce nec massa ac enim pellentesque ornare. Pellentesque non sapien varius, pellentesque tellus sit amet, facilisis justo. Duis rhoncus nunc id elementum dapibus. Sed dictum lacinia vestibulum.",
            post_title: "Lorem Event",
            meta_keys: {
                day: "20180428",
                time: "07:00:00",
                _meetup: "9",
                _rsvpNo: [
                    "robert",
                    "jjtime",
                    "username2"
                ],
                _rsvpYes: {
                    "cheeselover",
                    "neweradude",
                    "james1996"
                }
            }
        },
        ...
    ],
    meetups:[
        {
            ID: 9,
            post_content: "The nicest Meetup ever",
            post_title: "Tech Enthusiasts",
        },
        ...
    ],
    session:{
        ID: 2,
        username: "theUser",
        password: "1234",
        token: "qwerty12345asdfgzxcv"
    }
    ]
};
```

Para tener acceso a los datos globales, debe importar el contexto:
```jsx
// importa el contexto en el mismo fichero de tu vista
import { Context } from '/path/to/store/appContext.jsx';

const MyView = () => {
    // utiliza el hook useContext
    const { actions, store } = useContext(Context);
    //Luego puedes utilizar actions y store donde prefieras en el codigo de tu vista
    return (<span> hello, {store.events[0].post_title} </span>);
}

```

Todo tu Fetch/AJAX estará en la sección `useEffect()` del archivo appContext.jsx.

<onlyfor saas="false" withBanner="false">
	
## 🌱  Cómo iniciar este proyecto

No clones este repositorio porque usaremos una plantilla diferente.  

Recomendamos abrir el `react flux boilerplate`, utilizando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/es/lesson/tutorial-de-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternativamente, puedes clonar el repositorio de [GitHub](https://4geeks.com/es/how-to/como-clonar-un-repositorio-de-github) en tu computadora local utilizando el comando `git clone`.  

Este es el repositorio que necesitas abrir o clonar:  

```sh
$ git clone https://github.com/4GeeksAcademy/react-hello-webapp
```

1. No clones este repositorio. El primer paso para comenzar a codificar es clonar el [react flux boilerplate](https://github.com/4GeeksAcademy/react-hello-webapp) en tu computador local o con Gitpod.

💡 Importante: Recuerda actualizar el `remote` del proyecto con el de tu repositorio usando `git remote set-url origin <your new url>`, y luego guardar tu código en tu nuevo repositorio usando `add`, `commit` y `push`.

### Pasos

1. Instala las dependencias del proyecto con `$ npm install`

2. Ejecuta el servidor de desarrollo de webpack con `$ npm run start`

3. ¡Listo! Empieza a trabajar.

> _"El momento más espantoso es siempre antes de empezar."_
> -_Stephen King_

</onlyfor>
