---
title: Agregar una página de propiedades (ATL Tutorial, parte 6) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32b89b36318800ff35bc78fee35f094f75bdf36e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848696"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Agregar una página de propiedades (Tutorial de ATL, Parte 6)
Páginas de propiedades se implementan como objetos COM independientes, lo que permite compartirlas si es necesario. En este paso, realizará las tareas siguientes para agregar una página de propiedades al control:  
  
-   Crear el recurso de página de propiedades  
  
-   Agregar código para crear y administrar la página de propiedades  
  
-   Adición de la página de propiedades al Control  
  
## <a name="creating-the-property-page-resource"></a>Crear el recurso de página de propiedades  
 Para agregar una página de propiedades al control, use el Asistente para agregar clases de ATL.  
  
#### <a name="to-add-a-property-page"></a>Para agregar una página de propiedades  
  
1.  En el Explorador de soluciones, haga clic en polígono.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  En la lista de plantillas, seleccione **página de propiedades ATL** y haga clic en **agregar**.  
  
4.  Cuando aparezca el Asistente para páginas de propiedades ATL, escriba *PolyProp* como el **corto** nombre.  
  
5.  Haga clic en **cadenas** para abrir el **cadenas** página y escriba **& polígono** como el **título**.  
  
     El **título** de la propiedad de página es la cadena que aparece en la pestaña para esa página. El **cadena** es una descripción que utiliza un marco de propiedades para colocar en una sugerencia de línea o la herramienta de estado. Tenga en cuenta que el marco de propiedad estándar actualmente no usa esta cadena, por lo que puede dejar con el contenido predeterminado. No se generará un **archivo de Ayuda** en este momento, así que elimine la entrada en ese cuadro de texto.  
  
6.  Haga clic en **finalizar**, y se creará el objeto de la página de propiedad.  
  
 Se crean los tres archivos siguientes:  
  
|Archivo|Descripción|  
|----------|-----------------|  
|PolyProp.h|Contiene la clase de C++ `CPolyProp`, que implementa la página de propiedades.|  
|PolyProp.cpp|Incluye el archivo PolyProp.h.|  
|PolyProp.rgs|El script de registro que registra el objeto de la página de propiedad.|  
  
 También se realizan los cambios de código siguiente:  
  
-   La página de propiedades nuevo se agrega al mapa de entrada de objetos en Polygon.cpp.  
  
-   La `PolyProp` clase se agrega al archivo Polygon.idl.  
  
-   El nuevo archivo de script de registro PolyProp.rgs se agrega a los recursos del proyecto.  
  
-   Una plantilla de cuadro de diálogo se agrega a los recursos del proyecto para la página de propiedades.  
  
-   Las cadenas de propiedad que ha especificado se agregan a la tabla de cadenas de recursos.  
  
 Ahora agregue los campos que desea que aparezca en la página de propiedades.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Para agregar campos a la página de propiedades  
  
1.  En el Explorador de soluciones, haga doble clic en el archivo de recursos Polygon.rc. Se abrirá la vista de recursos.  
  
2.  En la vista de recursos, expanda el nodo de cuadro de diálogo y haga doble clic en IDD_POLYPROP. Tenga en cuenta que el cuadro de diálogo que aparece es vacío salvo por una etiqueta que indica si debe inserte aquí los controles.  
  
3.  Seleccione esa etiqueta y cámbiela a leer `Sides:` modificando el **título** texto en el **propiedades** ventana.  
  
4.  Cambiar el tamaño de etiqueta del cuadro de texto para que se ajuste el tamaño del texto.  
  
5.  Arrastre un control de edición del cuadro de herramientas a la derecha de la etiqueta.  
  
6.  Por último, cambie el **ID** de control de edición para `IDC_SIDES` mediante la ventana Propiedades.  
  
 Esto completa el proceso de crear el recurso de página de propiedades.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Agregar código para crear y administrar la página de propiedades  
 Ahora que ha creado el recurso de página de propiedades, tiene que escribir el código de implementación.  
  
 En primer lugar, habilite el `CPolyProp` clase para establecer el número de lados en el objeto cuando la **aplicar** está presionado.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Para modificar la función Apply para establecer el número de lados  
  
1.  Reemplace el `Apply` función en PolyProp.h con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Una página de propiedades puede tener más de un cliente asociado a él en cualquier momento, por lo que la `Apply` función recorre y llama a `put_Sides` en cada cliente con el valor recuperado desde el cuadro de edición. Usa el [CComQIPtr](../atl/reference/ccomqiptr-class.md) (clase), que lleva a cabo la `QueryInterface` en cada objeto que se va a obtener el `IPolyCtl` de la interfaz de la `IUnknown` interfaz (almacenados en el `m_ppUnk` matriz).  
  
 Ahora, el código comprueba esa configuración la `Sides` propiedad realmente funcionado. Si se produce un error, el código muestra un cuadro de mensaje muestra los detalles del error de la `IErrorInfo` interfaz. Normalmente, un contenedor solicita a un objeto para el `ISupportErrorInfo` interfaz y las llamadas `InterfaceSupportsErrorInfo` primero, para determinar si el objeto es compatible con la información de error de configuración. Puede omitir esta tarea.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) le ayuda a controlar automáticamente el recuento de referencias, por lo que no es necesario llamar a `Release` en la interfaz. `CComBSTR` le ayuda con el procesamiento de BSTR, por lo que no es necesario que realizar la última `SysFreeString` llamar. También usa una de las diferentes clases de conversión de cadenas, por lo que puede convertir el BSTR si es necesario (Esto es por eso es la macro USES_CONVERSION al principio de la función).  
  
 También deberá establecer la marca de modificado de la página de propiedad para indicar que el **aplicar** botón debe estar habilitado. Esto se produce cuando el usuario cambia el valor de la **lados** cuadro de edición.  
  
#### <a name="to-handle-the-apply-button"></a>Para controlar el botón Aplicar  
  
1.  En la vista de clases, haga clic en CPolyProp y haga clic en **propiedades** en el menú contextual.  
  
2.  En la ventana Propiedades, haga clic en el **eventos** icono.  
  
3.  Expanda el `IDC_SIDES` nodo en la lista de eventos.  
  
4.  Seleccione `EN_CHANGE`y en el menú desplegable a la derecha, haga clic en  **\<Agregar > OnEnChangeSides**. El `OnEnChangeSides` declaración del controlador se agregará a Polyprop.h y la implementación a Polyprop.cpp.  
  
 A continuación, modificará el controlador.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Para modificar el método OnEnChangeSides  
  
1.  Agregue el código siguiente en Polyprop.cpp a la `OnEnChangeSides` método (y eliminará cualquier código que el Asistente para poner allí):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` se llama cuando se envía un mensaje WM_COMMAND con la notificación EN_CHANGE para el `IDC_SIDES` control. `OnEnChangeSides` a continuación, llama a `SetDirty` y pasa TRUE para indicar que la página de propiedades ahora está desfasada y **aplicar** botón debe estar habilitado.  
  
## <a name="adding-the-property-page-to-the-control"></a>Adición de la página de propiedades al Control  
 El Asistente para agregar clases de ATL y el Asistente para páginas de propiedades ATL no agregan la página de propiedades al control por usted automáticamente, porque podría haber varios controles en el proyecto. Deberá agregar una entrada al mapa de propiedades del control.  
  
#### <a name="to-add-the-property-page"></a>Para agregar la página de propiedades  
  
1.  Abra PolyCtl.h y agregue esta línea al mapa de propiedades:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Asignación de propiedad del control ahora este aspecto:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Podría haber agregado una macro PROP_PAGE con el CLSID de la página de propiedades, pero si utiliza la macro PROP_ENTRY como se muestra, el `Sides` también se guarda el valor de propiedad cuando se guarda el control.  
  
 Los tres parámetros a la macro son la descripción de la propiedad, el DISPID de la propiedad y el CLSID de la página de propiedades que tiene la propiedad en él. Esto es útil si, por ejemplo, cargue el control en Visual Basic y establece el número de lados en tiempo de diseño. Dado que el número de lados se guarda, al volver a cargar el proyecto de Visual Basic, se restaurará el número de lados.  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
 Ahora, genere el control e insértelo en ActiveX Control Test Container. En el contenedor de prueba, en el **editar** menú, haga clic en **PolyCtl Class Object**. Aparece la página de propiedades; Haga clic en el **polígono** ficha.  
  
 El **aplicar** botón está deshabilitado inicialmente. Comience a escribir un valor en el **lados** cuadro y **aplicar** se habilitará el botón. Cuando haya terminado de escribir el valor, haga clic en el **aplicar** botón. La visualización cambia de control y el **aplicar** botón nuevo está deshabilitado. Pruebe a escribir un valor no válido. Verá un cuadro de mensaje que contiene la descripción del error que establece desde el `put_Sides` función.  
  
 A continuación, se colocará el control en una página Web.  
  
 [Vuelva al paso 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [con el paso 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

