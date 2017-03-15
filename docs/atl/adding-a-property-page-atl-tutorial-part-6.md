---
title: "Agregar una p&#225;gina de propiedades (Tutorial de ATL, Parte 6) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Agregar una p&#225;gina de propiedades (Tutorial de ATL, Parte 6)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las páginas de propiedades se implementan como objetos COM independientes, que permiten que sean compartidos si es necesario.  En este paso, realizará las tareas siguientes para agregar una página de propiedades al control:  
  
-   Crear el recurso de la página de propiedades  
  
-   Agregar código para crear y administrar la página de propiedades  
  
-   Agregar la página de propiedades al Control  
  
## Crear el recurso de la página de propiedades  
 Para agregar una página de propiedades al control, utilice el ATL agregan el asistente de clases.  
  
#### para agregar una página de propiedades  
  
1.  En el explorador de soluciones, haga clic con el botón secundario Polygon.  
  
2.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar clase**.  
  
3.  En la lista de plantillas, seleccione **Página de propiedades ATL** y haga clic **Agregar**.  
  
4.  Cuando aparezca el Asistente para páginas de propiedades ATL, entre en `PolyProp` como nombre de **Corto** .  
  
5.  Haga **clic en cadenas** para **abrir la** página de cadenas y **escriba el** &Polygon como **título.**  
  
     **Título** de la página de propiedades es la cadena que aparece en la pestaña para esa página.  **Cadena de Documento** es una descripción que un marco de propiedades utiliza para colocar en una línea de estado o una información sobre herramientas.  Observe que el cuadro estándar de propiedad no utiliza actualmente esta cadena, por lo que puede dejarlo con contenido predeterminado.  No generará **Archivo de ayuda** en el momento, de modo que elimine la entrada en dicho cuadro de texto.  
  
6.  Haga clic en **Finalizar**, y el objeto de la página de propiedades se creará.  
  
 se crean los tres archivos siguientes:  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|PolyProp.h|contiene la clase `CPolyProp`de C\+\+, que implementa la página de propiedades.|  
|PolyProp.cpp|incluye el archivo de PolyProp.h.|  
|PolyProp.rgs|El script de registro que registra el objeto de la página de propiedades.|  
  
 Los siguientes cambios de código también se realizan:  
  
-   La nueva página de propiedades se agrega a la entrada de objeto asignada en Polygon.cpp.  
  
-   La clase de `PolyProp` se agrega al archivo de Polygon.idl.  
  
-   El nuevo archivo de script PolyProp.rgs de registro se agrega al recurso del proyecto.  
  
-   Una plantilla de cuadro de diálogo se agrega al recurso del proyecto para la página de propiedades.  
  
-   Las cadenas de propiedad especificada se agregan a la tabla de cadenas de recursos.  
  
 Ahora agregue los campos que desea que aparezcan en la página de propiedades.  
  
#### para agregar campos a la página de propiedades  
  
1.  En el explorador de soluciones, haga doble clic en el archivo de recursos de Polygon.rc.  Se abrirá la vista de recursos.  
  
2.  En la, expanda el nodo dialog y haga doble clic en IDD\_POLYPROP.  Observe que el cuadro de diálogo que aparece está vacía salvo una etiqueta que indica a que inserte los controles aquí.  
  
3.  Seleccione la etiqueta y cámbiela para leer `lados:` modificando el texto de **Título** en la ventana de **Propiedades** .  
  
4.  Cambie el tamaño del cuadro de la etiqueta de modo que ajusta el tamaño del texto.  
  
5.  Arrastre un control de edición del cuadro de herramientas a la derecha de la etiqueta.  
  
6.  Finalmente, cambie **ID** del control de edición a `IDC_SIDES` mediante la ventana Propiedades.  
  
 Esto completa el proceso de crear el recurso de la página de propiedades.  
  
## Agregar código para crear y administrar la página de propiedades  
 Ahora que ha creado el recurso de la página de propiedades, debe escribir el código de implementación.  
  
 Primero, permite a la clase de `CPolyProp` para establecer el número de lados en el objeto cuando se presiona el botón de **Aplicar** .  
  
#### Para modificar el aplicar funcione para establecer el número de lados  
  
1.  reemplace la función de `Apply` en PolyProp.h con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Una página de propiedad puede tener más de un cliente conectado a ella a la vez, de modo que los bucles de la función de `Apply` alrededor y llama a `put_Sides` en cada cliente con el valor recuperado del cuadro de edición.  Utiliza la clase de [CComQIPtr](../atl/reference/ccomqiptr-class.md) , que realiza `QueryInterface` en cada objeto para obtener la interfaz de `IPolyCtl` de la interfaz de **IUnknown** \(almacenados en la matriz de `m_ppUnk` \).  
  
 El código comprueba ahora que funcionó establecer la propiedad de `Sides` realmente.  Si se produce un error, el código muestra un cuadro de mensaje que muestra los detalles de error de la interfaz de **IErrorInfo** .  Normalmente, un contenedor solicita un objeto la interfaz de **ISupportErrorInfo** y llama a `InterfaceSupportsErrorInfo` primero, determinar si el objeto admite la información de error de valor.  Puede omitir esta tarea.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) ayuda automáticamente controlando el recuento de referencias, por lo que no necesita llamar a `Release` en la interfaz.  `CComBSTR` ayuda con `BSTR` que procesa, por lo que no tendrá que realizar la llamada final de `SysFreeString` .  También puede utilizar una de las distintas clases de la conversión de cadenas, lo que puede convertir `BSTR` en caso necesario \(esta es la razón por la que la macro de `USES_CONVERSION` está al principio de la función\).  
  
 También debe establecer el mensaje modificado de la página de propiedades para indicar que el botón de **Aplicar** esté habilitado.  Esto sucede cuando el usuario cambia el valor en el cuadro de edición de **lados** .  
  
#### Para controlar el botón apply  
  
1.  En la vista de clases, haga clic con el botón secundario CPolyProp y haga clic **Propiedades** en el menú contextual.  
  
2.  En la ventana Propiedades, haga clic en el icono de **events** .  
  
3.  Expanda el nodo de `IDC_SIDES` en la lista.  
  
4.  `EN_CHANGE`seleccione y, en el menú desplegable situado a la derecha, haga clic en **Agregar OnEnChangeSides**.  La declaración del controlador de `OnEnChangeSides` se agregará a Polyprop.h, y la implementación de controlador a Polyprop.cpp.  
  
 A continuación, modificará el controlador.  
  
#### para modificar el método de OnEnChangeSides  
  
1.  Agregue el código siguiente en Polyprop.cpp al método de `OnEnChangeSides` \(que elimina cualquier código que el asistente desde allí\):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` se invoca cuando un mensaje de **WM\_COMMAND** se envía con la notificación de **EN\_CHANGE** para el control de `IDC_SIDES` .  `OnEnChangeSides` llamar `SetDirty` y pasa `TRUE` para indicar que la página de propiedades es modificada ahora y el botón de **Aplicar** debe estar habilitado.  
  
## Agregar la página de propiedades al Control  
 Los ATL agregan el asistente de clases y el Asistente para páginas de propiedades ATL no agrega la página de propiedades al control automáticamente, porque podría haber varios controles en el proyecto.  Necesitará agregar una entrada al mapa de propiedades del control.  
  
#### para agregar la página de propiedades  
  
1.  PolyCtl.h abierto y agregue esta línea a la propiedad asignada:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 La propiedad del control ahora asignada tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Se podría haber agregar una macro de `PROP_PAGE` con el CLSID de la página de propiedades, pero si utiliza la macro de `PROP_ENTRY` como se muestra, el valor de propiedad de `Sides` también se guarda cuando se guarda el control.  
  
 Los tres parámetros a la macro son la descripción de la propiedad, los DISPID para la propiedad, y el CLSID de la página de propiedades que tiene la propiedad.  Esto es útil si, por ejemplo, carga el control en Visual Basic y establezca el número de lados en tiempo de diseño.  Dado que guardan el número de lados, al cargar el proyecto de Visual Basic, restablecerán el número de lados.  
  
## Compilar y probar el Control  
 Compile ahora ese control y incrustarlo en el contenedor de prueba del control ActiveX.  En contenedor de prueba, en el menú de **Editar** , haga clic **objeto de la clase de PolyCtl**.  La página de propiedades aparecerá; haga clic en la pestaña de **polígono** .  
  
 el botón de **Aplicar** se deshabilita inicialmente.  Empieza a escribir un valor en el cuadro de **lados** y el botón de **Aplicar** será habilitado.  Cuando haya terminado de escribir el valor, haga clic en el botón de **Aplicar** .  Los cambios de presentación del control, y el botón de **Aplicar** se deshabilita de nuevo.  Pruebe a escribir un valor no válido.  Verá un cuadro de mensaje el contener de la descripción del error que establece de la función de `put_Sides` .  
  
 Siguiente, coloque el control en una página Web.  
  
 [De nuevo al paso 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [En el paso 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)