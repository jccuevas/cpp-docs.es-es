---
title: "Agregar una página de propiedades (ATL Tutorial, parte 6) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90023486dd8e34195b2dd9f8a788f3f76235d407
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Agregar una página de propiedades (Tutorial de ATL, Parte 6)
Páginas de propiedades se implementan como objetos COM independientes, lo que permite compartirlas si es necesario. En este paso, realizará las tareas siguientes para agregar una página de propiedades al control:  
  
-   Crear el recurso de página de propiedades  
  
-   Agregar código para crear y administrar la página de propiedades  
  
-   Agregar la página de propiedades al Control  
  
## <a name="creating-the-property-page-resource"></a>Crear el recurso de página de propiedades  
 Para agregar una página de propiedades al control, use el Asistente para agregar clases de ATL.  
  
#### <a name="to-add-a-property-page"></a>Para agregar una página de propiedades  
  
1.  En el Explorador de soluciones, haga clic en polígono.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  En la lista de plantillas, seleccione **página de propiedades ATL** y haga clic en **agregar**.  
  
4.  Cuando aparezca el Asistente para páginas de propiedades ATL, escriba `PolyProp` como el **corto** nombre.  
  
5.  Haga clic en **cadenas** para abrir el **cadenas** página e introduzca **& polígono** como el **título**.  
  
     El **título** de la propiedad página es la cadena que aparece en la ficha de esa página. El **cadena** es una descripción que un marco de propiedad se utiliza para colocar en una sugerencia de línea o la herramienta de estado. Tenga en cuenta que el marco de propiedad estándar actualmente no usa esta cadena, por lo que puede dejar con el contenido predeterminado. No generará una **archivo de Ayuda** en este momento, por lo que elimina la entrada en dicho cuadro de texto.  
  
6.  Haga clic en **finalizar**, y se creará el objeto de página de propiedades.  
  
 Se crean los tres archivos siguientes:  
  
|Archivo|Descripción|  
|----------|-----------------|  
|PolyProp.h|Contiene la clase de C++ `CPolyProp`, que implementa la página de propiedades.|  
|PolyProp.cpp|Incluye el archivo PolyProp.h.|  
|PolyProp.rgs|El script de registro que registra el objeto de página de propiedades.|  
  
 También se realizan los cambios en el código siguiente:  
  
-   La nueva página de propiedades se agrega a la asignación de entrada de objeto en Polygon.cpp.  
  
-   La `PolyProp` clase se agrega al archivo Polygon.idl.  
  
-   El nuevo archivo de script de registro PolyProp.rgs se agrega a los recursos del proyecto.  
  
-   Una plantilla de cuadro de diálogo se agrega a los recursos del proyecto para la página de propiedades.  
  
-   Las cadenas de propiedad que ha especificado se agregan a la tabla de cadenas de recursos.  
  
 Ahora, agregue los campos que desea que aparezca en la página de propiedades.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Para agregar campos a la página de propiedades  
  
1.  En el Explorador de soluciones, haga doble clic en el archivo de recurso Polygon.rc. Se abrirá la vista de recursos.  
  
2.  En la vista de recursos, expanda el nodo de cuadro de diálogo y haga doble clic en IDD_POLYPROP. Tenga en cuenta que el cuadro de diálogo que aparece está vacío, excepto por una etiqueta que indica si debe insertar aquí los controles.  
  
3.  Seleccione esa etiqueta y cámbiela por leer `Sides:` modificando la **título** texto en la **propiedades** ventana.  
  
4.  Redimensionar el cuadro de etiqueta para que se ajuste el tamaño del texto.  
  
5.  Arrastre un control de edición del cuadro de herramientas a la derecha de la etiqueta.  
  
6.  Por último, cambie el **identificador** de control de edición para `IDC_SIDES` mediante la ventana Propiedades.  
  
 Esto completa el proceso de crear el recurso de página de propiedades.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Agregar código para crear y administrar la página de propiedades  
 Ahora que ha creado el recurso de página de propiedades, debe escribir el código de implementación.  
  
 En primer lugar, habilite el `CPolyProp` clase para establecer el número de lados en el objeto cuando el **aplicar** se presiona el botón.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Para modificar la función Apply para establecer el número de lados  
  
1.  Reemplace el `Apply` función en PolyProp.h con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Una página de propiedades puede tener más de un cliente asociado a él en cualquier momento, por lo que la `Apply` función recorre y llama a `put_Sides` en cada cliente con el valor recuperado del cuadro de edición. Usa el [CComQIPtr](../atl/reference/ccomqiptr-class.md) (clase), que lleva a cabo la `QueryInterface` cada objeto que se va a obtener el `IPolyCtl` de la interfaz de la **IUnknown** interfaz (almacenados en la `m_ppUnk` matriz).  
  
 Ahora, el código comprueba esa configuración el `Sides` propiedad trabajada realmente. Si se produce un error, el código muestra un cuadro de mensaje muestra los detalles de error de la **IErrorInfo** interfaz. Normalmente, un contenedor solicita a un objeto para el **ISupportErrorInfo** interfaz y llamadas `InterfaceSupportsErrorInfo` primero, para determinar si el objeto es compatible con la información de error de configuración. Puede omitir esta tarea.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) le ayuda a controlando automáticamente el recuento de referencias, por lo que no es necesario llamar a `Release` en la interfaz. `CComBSTR`le ayuda a con `BSTR` de procesamiento, por lo que no es necesario que realizar la última `SysFreeString` llamar. También utilizamos una de las diferentes clases de conversión de cadenas, por lo que puede convertir el `BSTR` si es necesario (se trata de por qué la `USES_CONVERSION` macro está al principio de la función).  
  
 También debe establecer el marcador de modificado de la página de propiedades para indicar que la **aplicar** botón debe estar habilitado. Esto se produce cuando el usuario cambia el valor de la **lados** cuadro de edición.  
  
#### <a name="to-handle-the-apply-button"></a>Para controlar el botón Aplicar  
  
1.  En la vista de clases, haga clic en CPolyProp y haga clic en **propiedades** en el menú contextual.  
  
2.  En la ventana Propiedades, haga clic en el **eventos** icono.  
  
3.  Expanda el `IDC_SIDES` nodo en la lista de eventos.  
  
4.  Seleccione `EN_CHANGE`y en el menú desplegable a la derecha, haga clic en  **\<Agregar > OnEnChangeSides**. El `OnEnChangeSides` declaración del controlador se agregará a Polyprop.h y la implementación a Polyprop.cpp.  
  
 A continuación, modificará el controlador.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Para modificar el método OnEnChangeSides  
  
1.  Agregue el código siguiente en Polyprop.cpp a la `OnEnChangeSides` método (eliminar cualquier código que haya puesto allí el asistente):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides`se invocará cuando un **WM_COMMAND** mensaje se envía con el **EN_CHANGE** notificación para el `IDC_SIDES` control. `OnEnChangeSides`a continuación, llama `SetDirty` y pasa `TRUE` para indicar la propiedad de la página ahora está desfasada y **aplicar** botón debe estar habilitado.  
  
## <a name="adding-the-property-page-to-the-control"></a>Agregar la página de propiedades al Control  
 El Asistente para agregar clases de ATL y el Asistente para páginas de propiedades ATL no agregan la página de propiedades al control automáticamente automáticamente, ya que podría haber varios controles en el proyecto. Debe agregar una entrada a la asignación de propiedad del control.  
  
#### <a name="to-add-the-property-page"></a>Para agregar la página de propiedades  
  
1.  Abra PolyCtl.h y agregue esta línea al mapa de propiedades:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Asignación de propiedad del control ahora se ve así:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Podría haber agregado un `PROP_PAGE` macro con el CLSID de la página de propiedades, aunque si se usa el `PROP_ENTRY` macro tal y como se muestra, la `Sides` también se guarda el valor de propiedad cuando se guarda el control.  
  
 Los tres parámetros de la macro son la descripción de la propiedad, el identificador DISPID de la propiedad y el CLSID de la página de propiedades que tiene la propiedad en él. Esto es útil si, por ejemplo, cargue el control en Visual Basic y establecer el número de lados en tiempo de diseño. Dado que el número de lados se guarda, al volver a cargar el proyecto de Visual Basic, se restaurará el número de lados.  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
 Ahora, genere el control e insértelo en ActiveX Control Test Container. En el contenedor de prueba, en la **editar** menú, haga clic en **PolyCtl Class Object**. Aparece la página de propiedades; Haga clic en el **polígono** ficha.  
  
 El **aplicar** botón está inicialmente deshabilitado. Comience a escribir un valor en el **lados** cuadro y **aplicar** se habilitará el botón. Cuando haya terminado de escribir el valor, haga clic en el **aplicar** botón. Los cambios de presentación del control y el **aplicar** botón nuevo está deshabilitado. Pruebe a escribir un valor no válido. Verá un cuadro de mensaje que contiene la descripción del error que puede establecer desde el `put_Sides` función.  
  
 A continuación, se coloca el control en una página Web.  
  
 [Vuelva al paso 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [Al paso 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

