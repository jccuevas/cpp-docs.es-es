---
title: Implementar una página de propiedades (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 139bdd9076e99139f4da105b4bb2b375689efe15
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="example-implementing-a-property-page"></a>Ejemplo: Implementar una página de propiedades
Este ejemplo muestra cómo crear una página de propiedades que muestra (y permite cambiar) las propiedades de la [clases de documento](../mfc/document-classes.md) interfaz.  
  
 El ejemplo se basa en el [ejemplo ATLPages](../visual-cpp-samples.md).  
  
 Para completar este ejemplo, aprenderá lo siguiente:  
  
- [Agregar la clase de página de propiedades ATL](#vcconusing_the_atl_object_wizard) mediante el cuadro de diálogo Agregar clase y el Asistente para la página de propiedades de ATL.  
  
- [Editar el recurso de cuadro de diálogo](#vcconediting_the_dialog_resource) agregando nuevos controles para las propiedades interesantes de la **documento** interfaz.  
  
- [Agregar controladores de mensajes](#vcconadding_message_handlers) mantener el sitio de la página de propiedad informado de los cambios realizados por el usuario.  
  
-   Agregue algunos `#import` instrucciones y una definición de tipo en la [mantenimiento](#vcconhousekeeping) sección.  
  
- [Invalidar setObjects](#vcconoverriding_ipropertypageimpl_setobjects) para validar los objetos que se pasan a la página de propiedades.  
  
- [Reemplazar IPropertyPageImpl](#vcconoverriding_ipropertypageimpl_activate) para inicializar la interfaz de la página de propiedades.  
  
- [Reemplazar IPropertyPageImpl:: Apply](#vcconoverride_ipropertypageimpl_apply) para actualizar el objeto con los valores de propiedad más recientes.  
  
- [Mostrar la página de propiedades](#vccontesting_the_property_page) mediante la creación de un objeto auxiliar simple.  
  
- [Crear una macro](#vcconcreating_a_macro) que probará la página de propiedades.  
  
##  <a name="vcconusing_the_atl_object_wizard"></a> Agregar la clase de página de propiedades ATL  
 En primer lugar, cree un nuevo proyecto ATL para un servidor de archivo DLL denominado `ATLPages7`. Ahora use la [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) para generar una página de propiedades. Conceder a la página de propiedades un **nombre corto** de **DocProperties** , a continuación, cambie a la **cadenas** página para establecer elementos específicos de la página de propiedades como se muestra en la tabla siguiente.  
  
|Elemento|Valor|  
|----------|-----------|  
|Title|TextDocument|  
|Cadena de documento|Propiedades de TextDocument VCUE|  
|HelpFile|*\<en blanco >*|  
  
 Los valores que establezca en esta página del asistente se devolverán al contenedor de página de propiedades cuando llama a **IPropertyPage:: GetPageInfo**. ¿Qué ocurre con las cadenas una vez dependiente en el contenedor, pero normalmente se van a utilizar para identificar la página al usuario. El título suele aparecer en una ficha situada sobre la página y la cadena del documento se mostrarán en una barra de estado o información sobre herramientas (aunque el marco de propiedad estándar no utiliza esta cadena en absoluto).  
  
> [!NOTE]
>  Las cadenas que establezca aquí se almacenan como recursos de cadena en el proyecto por el asistente. Puede editar fácilmente estas cadenas mediante el editor de recursos si necesita cambiar esta información una vez generado el código de la página.  
  
 Haga clic en **Aceptar** para que el asistente genere la página de propiedades.  
  
##  <a name="vcconediting_the_dialog_resource"></a> Editar el recurso de cuadro de diálogo  
 Ahora que se ha generado la página de propiedades, debe agregar algunos controles para el recurso de cuadro de diálogo que representa la página. Agregar un cuadro de edición, un control de texto estático y una casilla de verificación y establezca sus identificadores como se muestra a continuación:  
  
 ![Edición de un recurso de cuadro de diálogo](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")  
  
 Estos controles se utilizará para mostrar el nombre de archivo del documento y su estado de sólo lectura.  
  
> [!NOTE]
>  El recurso de cuadro de diálogo no incluye un marco ni botones de comando ni tiene el aspecto con pestañas que podría haber esperado. Estas características son proporcionadas por un marco de página de propiedades como el que se creó mediante una llamada [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437).  
  
##  <a name="vcconadding_message_handlers"></a> Agregar controladores de mensajes  
 Con los controles en su lugar, puede agregar controladores de mensajes para actualizar el estado modificado de la página cuando cambia el valor de uno de los controles:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]  
  
 Este código responde a los cambios realizados en el control de edición o la casilla de verificación mediante una llamada a [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), que le informa de sitio de la página que ha cambiado la página. Normalmente el sitio de la página responderá habilitando o deshabilitando una **aplicar** botón en el marco de la página de propiedades.  
  
> [!NOTE]
>  En sus propias páginas de propiedades, deberá realizar un seguimiento de exactamente qué propiedades se han modificado por el usuario para que no puede actualizar las propiedades que no han cambiado. Este ejemplo implementa dicho código realizando el seguimiento de los valores de propiedad original y comparándolos con los valores actuales de la interfaz de usuario cuando llega el momento para aplicar los cambios.  
  
##  <a name="vcconhousekeeping"></a> Tareas de mantenimiento  
 Ahora agregue un par de `#import` instrucciones a DocProperties.h para que el compilador conoce el **documento** interfaz:  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]  
  
 También necesitará hacer referencia a la `IPropertyPageImpl` clase base; agregue lo siguiente `typedef` a la **CDocProperties** clase:  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Reemplazar setObjects  
 La primera `IPropertyPageImpl` es el método que es necesario invalidar [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). A continuación agregará código para comprobar que se ha pasado un único objeto y que admite la **documento** interfaz que espera:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  Tiene sentido para admitir un único objeto de esta página porque le permitirá al usuario establecer el nombre de archivo del objeto, un único archivo puede existir en cada ubicación.  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Reemplazar IPropertyPageImpl  
 El paso siguiente es inicializar la página de propiedades con los valores de propiedad del objeto subyacente cuando la página se crea por primera vez.  
  
 En este caso, deberá agregar a los miembros siguientes a la clase ya también utilizará los valores de propiedad iniciales para la comparación cuando los usuarios de la página aplicar sus cambios:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]  
  
 La implementación de la clase base de la [activar](../atl/reference/ipropertypageimpl-class.md#activate) método es responsable de crear el cuadro de diálogo y sus controles, por lo que puede invalidar este método y agregar su propia inicialización después de llamar a la clase base:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]  
  
 Este código usa los métodos COM de la **documento** interfaz para obtener las propiedades que le interesa. A continuación, utiliza los contenedores de la API de Win32 proporcionados por [CDialogImpl](../atl/reference/cdialogimpl-class.md) y sus clases base para mostrar los valores de propiedad para el usuario.  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Reemplazar IPropertyPageImpl:: Apply  
 Cuando los usuarios desean aplicar los cambios a los objetos, el sitio de la página de propiedades llamará el [aplicar](../atl/reference/ipropertypageimpl-class.md#apply) método. Éste es el lugar para hacer lo contrario del código de **activar** , mientras que **activar** tardó valores del objeto y ellos inserta en los controles en la página de propiedades, **aplicar** toma los valores de los controles en la página de propiedades y los envía en el objeto.  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  La comprobación con [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) al principio de esta implementación es una comprobación inicial para evitar actualizaciones innecesarias de los objetos si **aplicar** se llama más de una vez. También existen comprobaciones para cada uno de los valores de propiedad para asegurarse de que los únicos cambios que se producen en una llamada de método a la **documento**.  
  
> [!NOTE]
> **Documento** expone **FullName** como una propiedad de solo lectura. Para actualizar el nombre de archivo del documento en función de los cambios realizados en la página de propiedades, tiene que utilizar el **guardar** método para guardar el archivo con un nombre diferente. Por lo tanto, no tiene el código en una página de propiedades limita a obtener o establecer las propiedades.  
  
##  <a name="vccontesting_the_property_page"></a> Mostrar la página de propiedades  
 Para mostrar esta página, debe crear un objeto auxiliar simple. El objeto auxiliar proporcionará un método que simplifica la **OleCreatePropertyFrame** API para mostrar una sola página conectada a un único objeto. Esta aplicación auxiliar se va a diseñar para que se puede usar desde Visual Basic.  
  
 Utilice la [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md) para generar una nueva clase y usar `Helper` como su nombre corto. Una vez creado, agregue un método tal como se muestra en la tabla siguiente.  
  
|Elemento|Valor|  
|----------|-----------|  
|Nombre del método|`ShowPage`|  
|Parámetros|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 El `bstrCaption` parámetro es el título que se mostrará como título del cuadro de diálogo. El `bstrID` parámetro es una cadena que representa un CLSID o ProgID de la página de propiedades para mostrar. El `pUnk` parámetro será el `IUnknown` puntero del objeto cuyas propiedades se configurará mediante la página de propiedades.  
  
 Implemente el método tal como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a> Crear una Macro  
 Una vez que haya generado el proyecto, puede probar la página de propiedades y el objeto auxiliar mediante una sencilla macro que puede crear y ejecutar en el entorno de desarrollo de Visual Studio. Esta macro creará una aplicación auxiliar de objeto y después llamar a su **ShowPage** método utilizando el ProgID de la **DocProperties** página de propiedades y el **IUnknown** puntero del documento actualmente activas en el editor de Visual Studio. El código que necesita para esta macro se muestra a continuación:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
 
Public Module AtlPages  
 
    Public Sub Test()  
    Dim Helper  
    Helper = CreateObject("ATLPages7.Helper.1")  
 
    On Error Resume Next  
    Helper.ShowPage(_ 
    ActiveDocument.Name,
    _ 
 "ATLPages7Lib.DocumentProperties.1",
    _ 
    DTE.ActiveDocument _)  
    End Sub  
 
End Module  
```  
  
 Al ejecutar esta macro, se mostrará la página de propiedades que muestra el nombre de archivo y el estado de sólo lectura del documento de texto actualmente activo. El estado de sólo lectura del documento sólo refleja la capacidad para escribir en el documento en el entorno de desarrollo; Esto no afecta el atributo de sólo lectura del archivo en disco.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../visual-cpp-samples.md)

