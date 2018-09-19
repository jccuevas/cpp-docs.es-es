---
title: Implementación de una página de propiedades (ATL) | Microsoft Docs
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
ms.openlocfilehash: 36d3289767d8c8e2eaa2f25889aaff073cf73fce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046256"
---
# <a name="example-implementing-a-property-page"></a>Ejemplo: Implementar una página de propiedades

En este ejemplo se muestra cómo crear una página de propiedades que muestra las propiedades de (y le permite cambiar) la [clases de documento](../mfc/document-classes.md) interfaz.

En el ejemplo se basa en el [ejemplo ATLPages](../visual-cpp-samples.md).

Para completar este ejemplo, hará lo siguiente:

- [Agregue la clase de página de propiedades ATL](#vcconusing_the_atl_object_wizard) mediante el cuadro de diálogo Agregar clase y el Asistente para páginas de propiedades ATL.

- [Editar el recurso de cuadro de diálogo](#vcconediting_the_dialog_resource) agregando nuevos controles para las propiedades de la `Document` interfaz.

- [Agregar controladores de mensajes](#vcconadding_message_handlers) mantener el sitio de la página de propiedad informará de los cambios realizados por el usuario.

- Agregue algunos `#import` instrucciones y una definición de tipo en el [mantenimiento](#vcconhousekeeping) sección.

- [Invalidar setObjects](#vcconoverriding_ipropertypageimpl_setobjects) para validar los objetos que se pasan a la página de propiedades.

- [Invalidar IPropertyPageImpl](#vcconoverriding_ipropertypageimpl_activate) para inicializar la interfaz de la página de propiedades.

- [Reemplazar IPropertyPageImpl:: Apply](#vcconoverride_ipropertypageimpl_apply) para actualizar el objeto con los valores de propiedad más recientes.

- [Mostrar la página de propiedades](#vccontesting_the_property_page) mediante la creación de un objeto auxiliar simple.

- [Crear una macro](#vcconcreating_a_macro) que probará la página de propiedades.

##  <a name="vcconusing_the_atl_object_wizard"></a> Adición de la clase de página de propiedades ATL

En primer lugar, cree un nuevo proyecto ATL para un servidor de archivo DLL denominado `ATLPages7`. Ahora utilice el [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) para generar una página de propiedades. Asigne a la página de propiedades una **nombre corto** de **DocProperties** , a continuación, cambie a la **cadenas** página para establecer elementos específicos de la página de propiedad, como se muestra en la tabla siguiente.

|Elemento|Valor|
|----------|-----------|
|Title|TextDocument|
|Cadena de documento|Propiedades de TextDocument VCUE|
|HelpFile|*\<en blanco >*|

Los valores que establezca en esta página del asistente se devolverán en el contenedor de la página de propiedad cuando llama a `IPropertyPage::GetPageInfo`. ¿Qué ocurre con las cadenas después de que es dependiente en el contenedor, pero normalmente se usará para identificar la página al usuario. El título suele aparecer en una pestaña situada sobre la página y la cadena de documento puede mostrarse en una barra de estado o información sobre herramientas (aunque el marco de propiedad estándar no usa esta cadena en absoluto).

> [!NOTE]
>  Las cadenas que establezca aquí se almacenan como recursos de cadena en el proyecto por el asistente. Puede editar fácilmente estas cadenas mediante el editor de recursos si necesita cambiar esta información una vez generado el código de la página.

Haga clic en **Aceptar** que el Asistente para generar la página de propiedades.

##  <a name="vcconediting_the_dialog_resource"></a> El recurso de cuadro de diálogo de edición

Ahora que se ha generado la página de propiedades, deberá agregar algunos controles para el recurso de cuadro de diálogo que representa la página. Agregue un cuadro de edición, un control de texto estático y una casilla de verificación y establezca sus identificadores como se muestra a continuación:

![Edición de un recurso de cuadro de diálogo](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")

Estos controles se usará para mostrar el nombre de archivo del documento y su estado de solo lectura.

> [!NOTE]
>  El recurso de cuadro de diálogo no incluye un marco ni botones de comando ni tiene el aspecto con pestañas que se podría esperar. Estas características son proporcionadas por un marco de página de propiedades como el que se creó mediante una llamada a [OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe).

##  <a name="vcconadding_message_handlers"></a> Agregar controladores de mensajes

Con los controles en su lugar, puede agregar controladores de mensajes para actualizar el estado modificado de la página cuando cambia el valor de cualquiera de los controles:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Este código responde a los cambios realizados en el control de edición o la casilla de verificación mediante una llamada a [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), que informa al sitio de la página que ha cambiado la página. Normalmente, el sitio de la página responderá habilitando o deshabilitando una **aplicar** botón en el marco de la página de propiedades.

> [!NOTE]
>  En sus propias páginas de propiedades, debe realizar un seguimiento de forma precisa las propiedades que se han modificado por el usuario para que no puede actualizar las propiedades que no han cambiado. En este ejemplo se implementa ese código al realizar el seguimiento de los valores de propiedad originales y compararlos con los valores actuales de la interfaz de usuario cuando llega el momento de aplicar los cambios.

##  <a name="vcconhousekeeping"></a> Tareas de mantenimiento

Ahora agregue un par de `#import` DocProperties.h instrucciones para que el compilador conoce el `Document` interfaz:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

También tendrá que hacer referencia a la `IPropertyPageImpl` clase base; agregue las siguientes **typedef** a la `CDocProperties` clase:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Reemplazar setObjects

La primera `IPropertyPageImpl` es el método que es necesario reemplazar [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). A continuación, agregará código para comprobar que se ha pasado un único objeto y que admite el `Document` interfaz que espera:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Tiene sentido para admitir un único objeto de esta página porque permitirá al usuario establecer el nombre de archivo del objeto, un único archivo puede existir en cualquier ubicación.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Reemplazar IPropertyPageImpl

El siguiente paso es inicializar la página de propiedades con los valores de propiedad del objeto subyacente cuando se crea por primera vez la página.

En este caso, deberá agregar a los miembros siguientes a la clase ya también usará los valores de propiedad iniciales para la comparación cuando los usuarios de la página aplicar sus cambios:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

La implementación de clase base la [activar](../atl/reference/ipropertypageimpl-class.md#activate) método es responsable de crear el cuadro de diálogo y sus controles, por lo que puede invalidar este método y agregar su propia inicialización después de llamar a la clase base:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Este código usa los métodos COM de la `Document` interfaz para obtener las propiedades que le interesa. A continuación, utiliza los contenedores de la API de Win32 proporcionados por [CDialogImpl](../atl/reference/cdialogimpl-class.md) y sus clases base para mostrar los valores de propiedad para el usuario.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Reemplazar IPropertyPageImpl:: Apply

Cuando los usuarios desean aplicar sus cambios a los objetos, el sitio de la página de propiedad llamará el [aplicar](../atl/reference/ipropertypageimpl-class.md#apply) método. Este es el lugar para realizar el proceso inverso del código en `Activate` , mientras que `Activate` tardó valores del objeto y los inserta en los controles en la página de propiedades, `Apply` toma los valores de los controles en la página de propiedades y los inserta en la objeto.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  La comprobación en [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) al principio de esta implementación es una comprobación inicial para evitar las actualizaciones innecesarias de los objetos si `Apply` se llama más de una vez. También existen comprobaciones para cada uno de los valores de propiedad para asegurarse de que solo los cambios como resultado una llamada al método el `Document`.

> [!NOTE]
> `Document` expone `FullName` como una propiedad de solo lectura. Para actualizar el nombre de archivo del documento en función de los cambios realizados en la página de propiedades, tiene que usar el `Save` método para guardar el archivo con un nombre diferente. Por lo tanto, no tiene el código en una página de propiedades limita a obtener o establecer propiedades.

##  <a name="vccontesting_the_property_page"></a> Mostrar la página de propiedades

Para mostrar esta página, deberá crear un objeto auxiliar simple. El objeto auxiliar proporcionará un método que simplifica la `OleCreatePropertyFrame` API para mostrar una sola página conectado a un único objeto. Esta aplicación auxiliar se va a diseñar para que se puede usar desde Visual Basic.

Utilice la [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md) para generar una nueva clase y usar `Helper` como su nombre corto. Una vez creado, agregue un método tal como se muestra en la tabla siguiente.

|Elemento|Valor|
|----------|-----------|
|Nombre del método|`ShowPage`|
|Parámetros|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

El *bstrCaption* parámetro es el título que se mostrará como título del cuadro de diálogo. El *bstrID* parámetro es una cadena que representa un CLSID o ProgID de la página de propiedades para mostrar. El *pUnk* parámetro será el `IUnknown` puntero del objeto cuyas propiedades se configurarán por la página de propiedades.

Implemente el método tal como se muestra a continuación:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> Creación de una Macro

Una vez que ha creado el proyecto, puede probar la página de propiedades y el objeto auxiliar mediante una macro sencilla que puede crear y ejecutar en el entorno de desarrollo de Visual Studio. Esta macro creará una aplicación auxiliar de objeto y, después, llame a su `ShowPage` método utilizando el ProgID de la **DocProperties** página de propiedades y el `IUnknown` puntero del documento activo actualmente en el editor de Visual Studio. El código que necesita para esta macro se muestra a continuación:

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

Al ejecutar esta macro, se mostrará la página de propiedades que muestra el nombre de archivo y el estado de solo lectura del documento de texto actualmente activo. El estado de solo lectura del documento sólo refleja la capacidad para escribir en el documento en el entorno de desarrollo; Esto no afecta el atributo de sólo lectura del archivo en disco.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../atl/atl-com-property-pages.md)<br/>
[Ejemplo ATLPages](../visual-cpp-samples.md)
