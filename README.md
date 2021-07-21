# Practica08-Laberinto-VR
Practica 8

Crear la GVR Camera Rig Durante este paso, crearemos la cámara VR incluyendo el GvrEditorEmulator en la escena y configurando la cámara.
1. Agregue el objeto prefab GvrEditorEmulator a la escena

![image](https://user-images.githubusercontent.com/49033606/126434489-f9513019-ccad-4cbc-bdd3-ec5443bea5e6.png)

2. Convierta el objeto Main Camera en un elemento hijo del objeto GvrEditorEmulator.

![image](https://user-images.githubusercontent.com/49033606/126434680-73ca00c2-015b-431d-88a8-a7bfbe9ecef4.png)

3. Restablece el componente Transformar del objeto Main Camera
4. Mueva el objeto GvrEditorEmulator a una ubicación conveniente para el desarrollo, por ejemplo, Posición: 0, 3, 35 y Rotación: 0, 180, 0.

![image](https://user-images.githubusercontent.com/49033606/126435138-0eb3a18c-8ca7-4c1d-8221-db50f62879b7.png)

Preparando la escena para la interacción Durante este paso, prepararemos la escena para la interacción configurando el puntero, el emisor de rayos y el sistema de eventos, y luego probaremos el sistema de punto de referencia incluido (waypoint).

1. Agregue el objeto prefab GvrReticlePointer a la escena como elemento secundario del objeto del Main Camera.

![image](https://user-images.githubusercontent.com/49033606/126434680-73ca00c2-015b-431d-88a8-a7bfbe9ecef4.png)

2. Aumente el valor de Distancia máxima de retícula para el GvrReticlePointer del valor predeterminado de 10 a 20.

![image](https://user-images.githubusercontent.com/49033606/126435209-c852227a-f957-462a-bdd1-51c4e5a399cb.png)

3. Agregue el script GvrPointerPhysicsRaycaster como componente en el objeto Main Camera.

![image](https://user-images.githubusercontent.com/49033606/126435405-ac9aca30-9d4f-40cb-8b40-fe287c7e0fe5.png)

4. Agregue el objeto prefab GvrEventSystem a la escena.

![image](https://user-images.githubusercontent.com/49033606/126435475-000b48ac-5f3f-4d27-aea4-5ec4fe74feb5.png)

5. Ingrese al modo de juego y navegue por la escena haciendo clic en los puntos de referencia.

![image](https://user-images.githubusercontent.com/49033606/126435647-c86c85f0-cde4-4d1e-8dde-2070b81aaa5c.png)

Hacer que los objetos del juego sean interactivos Durante este paso haremos que la Moneda, la Llave y la Puerta sean interactivas añadiéndoles componentes de disparadores y eventos.

1. Localiza y selecciona el objeto Coin en la jerarquía.

![image](https://user-images.githubusercontent.com/49033606/126435864-3a542a30-9f98-43d4-8283-efe0a08f44ff.png)

2. Verifique que tenga un componente Collider.

![image](https://user-images.githubusercontent.com/49033606/126435966-5bf9611f-23e9-4346-942e-99f50a786a98.png)

3. Agregue el script Coin proporcionado como componente.

![image](https://user-images.githubusercontent.com/49033606/126436065-367a9824-2b1f-40fc-9f49-601f11089d2b.png)

4. Agregue un dispardor de evento (Event Trigger) como componente
5. Agregue el evento PointerClick al componente Event Trigger.
6. Asigne el componente del script Coin al campo de objeto del evento Pointer Click
7. Asigne el método Coin.OnCoinClicked () como la función para el evento Pointer Click.

![image](https://user-images.githubusercontent.com/49033606/126436155-97824a1b-dd0f-4b2b-ab63-999212557b1d.png)

8. Ingrese al modo de juego, haga clic en la moneda y verifique que el mensaje 'Coin.OnCoinClicked ()' esté impreso en la ventana de la consola.

![image](https://user-images.githubusercontent.com/49033606/126436540-0e449c8a-a332-4465-8bef-0bb25e6f58cd.png)

9. Repita el mismo proceso para el objeto del juego Key pero use el script Key y el método Key.OnKeyClicked ().

![image](https://user-images.githubusercontent.com/49033606/126436970-7a65c099-c173-487f-a3e4-b64b93210275.png)

10. Repita el mismo proceso para el primer objeto principal del juego de Puerta, pero use el script de Puerta y el método Door.OnDoorClicked ().

![image](https://user-images.githubusercontent.com/49033606/126437129-695e336c-4292-4812-9a38-8d762a33909e.png)


Hacer la interfaz de usuario interactiva Durante este paso, haremos que el objeto SignPost sea interactivo al agregarle componentes de disparadores y eventos. El proceso es casi idéntico al que hicimos con la moneda, la llave y la puerta en el paso anterior, pero no necesitamos un colisionador para interactuar con los objetos del juego de la interfaz de usuario. En su lugar, debemos verificar que el objeto del juego Canvas tenga un componente Graphic Raycaster, y debido a que estamos usando GVR, reemplazaremos el Graphic Raycaster de Unity con el GvrPointerGraphicRaycaster de Google VR.

1. Localiza y selecciona el objeto del juego SignPost en la jerarquía.

![image](https://user-images.githubusercontent.com/49033606/126437414-67f66a45-4faa-4588-83c9-b4546f3685a4.png)


2. Elimine el componente Graphic Raycaster que se agrega automáticamente al crear un nuevo objeto.
3. Agregue el script GvrPointerGraphicRaycaster como componente.
4. Agregue el script SignPost proporcionado como componente.
5. Agregue un Event Trigger como componente.
6. Agregue el evento PointerClick al componente Event Trigger.
7. Asigne el componente script SignPost al campo de objeto del evento Pointer Click.
8. Asigne el método SignPost.ResetScene () como la función para el evento Pointer Click.

![image](https://user-images.githubusercontent.com/49033606/126437856-cd9b71c7-009a-4c6e-ba08-16d9470bb4cc.png)

9. Ingrese al modo de juego, haga clic en SignPost y verifique que el mensaje 'SignPost.ResetScene ()' esté impreso en la ventana de la consola. Programando el comportamiento de la moneda (coin) Durante este paso, programaremos el comportamiento de la moneda para que, cuando se haga clic en una moneda (coin), se reproduzca un sonido, muestre un efecto de "poof" y desaparezca.
10. Hay un mínimo de cinco monedas en el laberinto. Cuando se hace clic en una moneda, se reproduce un efecto de sonido en la ubicación de esa moneda.Cuando se hace clic en una moneda, esa moneda se elimina de la jerarquía de la escena.
11. Abra el script de Coin y lea todo el script, incluidos todos los comentarios.
12. Dedique un tiempo a comprender el comportamiento del objeto prefab CoinPoof proporcionado. Puede hacer esto, por ejemplo, ingresando al modo de juego y arrastrando un objeto prefab CoinPoof a la escena.
13. Programe el comportamiento de la moneda completando todos los comentarios TODO en el script.

![image](https://user-images.githubusercontent.com/49033606/126438230-e964f001-6b97-4419-b2d4-07e24069ffd5.png)

Programando el comportamiento de la puerta (door) Durante este paso, programaremos el comportamiento de la puerta (door) para que cuando se haga clic en la llave (key), la Puerta se desbloquee y cuando se haga clic en la Puerta, se escuche un sonido y comience a girar a una posición de apertura.
1. La puerta evita que el usuario navegue al objeto SignPost hasta que se haya abierto. Cuando comienza el juego, la puerta está bloqueada y cerrada. La puerta no se puede abrir cuando está bloqueada. La puerta solo puede desbloquearse haciendo clic en la llave. Cuando se hace clic y se desbloquea la puerta, la puerta comienza a abrirse. Cuando la puerta comienza a abrirse, se reproduce un efecto de sonido en la ubicación de la puerta. La puerta se anima a una posición de abierta solo por código, es decir, no mediante el uso de animación y controlador de animador.
2. Abra el script Door y lea todo el script, incluidos todos los comentarios.
3. Agregue un componente AudioSource al primer objeto padre Door y desactive la propiedad Play On Awake.
4. Asigne el audio Door_Opening al campo AudioClip.
5. Programe el comportamiento de la puerta completando todos los comentarios TODO en el script.

![image](https://user-images.githubusercontent.com/49033606/126438681-76dbe543-0675-4ecf-b08a-06f678756ddd.png)



Programando el comportamiento del SignPost Durante este paso, programaremos el comportamiento de SignPost para que cuando se haga clic en SignPost se reinicie el juego.

1. El SignPost no se puede ver ni interactuar antes de que se abra la puerta. Cuando se hace clic en SignPost, la escena se restablece a su estado inicial para que el juego se pueda volver a jugar.
2. Abra el script SignPost y lea todo el script, incluidos todos los comentarios.
3. Programe el comportamiento SignPost completando todos los comentarios TODO en el script.

![image](https://user-images.githubusercontent.com/49033606/126438806-ec1c4a3a-d5dc-4bc5-a4e1-9148bf1808c1.png)

Crear la funcionalidad del juego Durante este paso, armaremos todo y convertiremos nuestro proyecto en un juego real. Waypoints • El laberinto está diseñado de tal manera que el usuario no puede identificar una ruta a la llave desde la posición de inicio.

![image](https://user-images.githubusercontent.com/49033606/126438900-a78b8d04-32a8-4150-939e-c9f55c8bbdc5.png)






