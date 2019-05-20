---
title: Implementación de una página de propiedades (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 1f2c0387cd0a78ad0179e251654d2fa82b1eef13
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707098"
---
# <a name="example-implementing-a-property-page"></a>Ejemplo: Implementación de una página de propiedades

::: moniker range="vs-2019"

El Asistente para páginas de propiedades ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

En este ejemplo puede ver cómo crear una página de propiedades que muestre (y le permita cambiar) propiedades de la interfaz [Clases de documento](../mfc/document-classes.md).

El ejemplo se basa en el [ejemplo ATPages](../overview/visual-cpp-samples.md).

Para completar este ejemplo, hará lo siguiente:

- [Agregar la clase de la página de propiedades ATL](#vcconusing_the_atl_object_wizard) mediante el cuadro de diálogo Agregar clase y el Asistente para páginas de propiedades ATL.

- [Editar el recurso de diálogo](#vcconediting_the_dialog_resource) agregando nuevos controles para las propiedades interesantes de la interfaz `Document`.

- [Agregar controladores de mensajes](#vcconadding_message_handlers) para mantener informado al sitio de la página de propiedades de los cambios realizados por el usuario.

- Agregar algunas instrucciones `#import` y un typedef en la sección [Mantenimiento](#vcconhousekeeping).

- [Invalidar IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) para validar los objetos que se pasan a la página de propiedades.

- [Invalidar IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) para inicializar la interfaz de la página de propiedades.

- [Invalidar IPropertyPageImpl:: Apply](#vcconoverride_ipropertypageimpl_apply) para actualizar el objeto con los valores de propiedad más recientes.

- [Mostrar la página de propiedades](#vccontesting_the_property_page) creando un objeto auxiliar sencillo.

- [Crear una macro](#vcconcreating_a_macro) que probará la página de propiedades.

##  <a name="vcconusing_the_atl_object_wizard"></a> Adición de la clase de la página de propiedades ATL

En primer lugar, cree un nuevo proyecto ATL para un servidor DLL llamado `ATLPages7`. Ahora utilice el [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) para generar una página de propiedades. Asigne a la página de propiedades un **Nombre corto** de **DocProperties** y, a continuación, cambie a la página **Cadenas** para establecer elementos específicos de la página de propiedades como se muestra en la siguiente tabla.

|Elemento|Valor|
|----------|-----------|
|Title|TextDocument|
|Cadena de documento|Propiedades VCUE TextDocument|
|Archivo de ayuda|*\<blank>*|

Los valores que establezca en esta página del asistente se devolverán al contenedor de la página de propiedades cuando llame a `IPropertyPage::GetPageInfo`. Lo que les ocurra a las cadenas después de eso dependerá del contenedor, pero normalmente se usarán para identificar su página para el usuario. El título suele aparecer en una pestaña situada sobre su página y la cadena de documento se puede mostrar en una barra de estado o en la información sobre herramientas (aunque el marco de propiedades no usa esta cadena en absoluto).

> [!NOTE]
>  El asistente almacenará las cadenas que establezca aquí como recursos de cadena en el proyecto. Puede editar fácilmente estas cadenas mediante el editor de recursos si tiene que cambiar esta información una vez que se haya generado el código para su página.

Haga clic en **Aceptar** para que el asistente genere su página de propiedades.

##  <a name="vcconediting_the_dialog_resource"></a> Edición del recurso de diálogo

Ahora que se ha generado su página de propiedades, tendrá que agregar algunos controles al recurso de diálogo que represente su página. Agregue un cuadro de edición, un control de texto estático y una casilla, y establezca sus identificadores como se muestra a continuación:

![Edición de un recurso de diálogo](../atl/media/ppgresourcelabeled.gif "Editing a dialog resource")

Estos controles se usarán para mostrar el nombre de archivo del documento y su estado de solo lectura.

> [!NOTE]
>  El recurso de diálogo no incluye un marco ni botones de comando, ni tampoco tiene pestañas como tal vez haya imaginado. Un marco de la página de propiedades como el que se creó llamando a [OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe) proporciona estas características.

##  <a name="vcconadding_message_handlers"></a> Adición de controladores de mensajes

Con los controles en contexto, puede agregar controladores de mensajes para actualizar el estado con errores de la página al cambiar el valor de cualquiera de los controles:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Este código responde a los cambios realizados en la casilla o control de edición llamando a [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), que informa al sitio de la página de que esta ha cambiado. Normalmente, el sitio de la página responderá habilitando o deshabilitando el botón **Aplicar** en el marco de la página de propiedades.

> [!NOTE]
>  En sus propias páginas, es posible que tenga que realizar un seguimiento de exactamente las propiedades que el usuario ha modificado para que pueda evitar la actualización de las propiedades sin cambios. En este ejemplo se implementa ese código realizando un seguimiento de los valores de propiedad originales y comparándolos con los valores actuales desde la interfaz de usuario en el momento de aplicarse los cambios.

##  <a name="vcconhousekeeping"></a> Mantenimiento

Ahora agregue un par de instrucciones `#import` a DocProperties.h para que el compilador conozca la interfaz `Document`:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

También tendrá que hacer referencia a la clase base `IPropertyPageImpl`; agregue el siguiente **typedef** a la clase `CDocProperties`:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Invalidación de IPropertyPageImpl::SetObjects

El primer método `IPropertyPageImpl` que debe invalidar es [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Aquí agregará código para comprobar que solo se ha pasado un único objeto y que admite la interfaz `Document` que espera:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Tiene sentido admitir solo un único objeto para esta página, ya que permitirá al usuario establecer el nombre de archivo del objeto. Solo puede existir un archivo en cualquier ubicación.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Invalidación de IPropertyPageImpl::Activate

El siguiente paso consiste en inicializar la página de propiedades con los valores de propiedad del objeto subyacente la primera vez que se crea la página.

En este caso, debe agregar los siguientes miembros a la clase, ya que también usará los valores de propiedad iniciales para la comparación cuando los usuarios de la página apliquen sus cambios:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

La implementación de la clase base del método [Activate](../atl/reference/ipropertypageimpl-class.md#activate) es responsable de la creación del cuadro de diálogo y sus controles, por lo que puede invalidar este método y agregar su propia inicialización después de llamar a la clase base:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Este código usa los métodos COM de la interfaz `Document` para obtener las propiedades que le interesan. A continuación, usa los contenedores de la API Win32 que proporciona [CDialogImpl](../atl/reference/cdialogimpl-class.md) y su clase base para mostrar los valores de propiedad al usuario.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Invalidación de IPropertyPageImpl::Apply

Cuando los usuarios deseen aplicar sus cambios a los objetos, el sitio de la página de propiedades llamará al método [Apply](../atl/reference/ipropertypageimpl-class.md#apply). Este es el lugar en el que realizar el proceso inverso del código en `Activate` (mientras que `Activate` tomó valores del objeto y los insertó en los controles de la página de propiedades, `Apply` toma valores de los controles de la página de propiedades y los inserta en el objeto).

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  La comparación con [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) al principio de esta implementación es una comprobación inicial para evitar actualizaciones innecesarias de los objetos si se llama a `Apply` más de una vez. Asimismo se realizan comparaciones con cada uno de los valores de propiedad para asegurarse de que solo los cambios dan como resultado una llamada de método a `Document`.

> [!NOTE]
> `Document` expone `FullName` como propiedad de solo lectura. Para actualizar el nombre de archivo del documento en función de los cambios realizados en la página de propiedades, debe usar el método `Save` para guardar el archivo con otro nombre. Por tanto, el código de una página de propiedades no tiene por qué limitarse a obtener o establecer propiedades.

##  <a name="vccontesting_the_property_page"></a> Visualización de la página de propiedades

Para mostrar esta página, debe crear un objeto auxiliar sencillo. El objeto auxiliar proporcionará un método que simplifica la API `OleCreatePropertyFrame` para mostrar una sola página conectada a un único objeto. Este asistente se diseñará para que pueda usarse desde Visual Basic.

Utilice el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md) para generar una nueva clase y usar `Helper` como su nombre corto. Una vez creada, agregue un método como se muestra en la siguiente tabla.

|Elemento|Valor|
|----------|-----------|
|Nombre del método|`ShowPage`|
|Parámetros|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

El parámetro *bstrCaption* es el título que se va a mostrar como título del cuadro de diálogo. El parámetro *bstrID* es una cadena que representa un CLSID o un ProgID de la página de propiedades que se va a mostrar. El parámetro *pUnk* será el puntero `IUnknown` del objeto cuyas propiedades configurará la página de propiedades.

Implemente el método como se muestra a continuación:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> Creación de una macro

Una vez que ha creado el proyecto, puede probar la página de propiedades y el objeto auxiliar mediante una macro sencilla que puede crear y ejecutar en el entorno de desarrollo de Visual Studio. Esta macro creará un objeto auxiliar y, a continuación, llamará a su método `ShowPage` mediante el ProgID de la página de propiedades **DocProperties** y el puntero `IUnknown` del documento actualmente activo en el editor de Visual Studio. El código que necesita para esta macro se muestra a continuación:

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

Al ejecutar esta macro, la página de propiedades aparecerá mostrando el nombre de archivo y el estado de solo lectura del documento de texto actualmente activo. El estado de solo lectura del documento solo refleja la capacidad de escribir en el documento en el entorno de desarrollo; no afecta al atributo de solo lectura del archivo en el disco.

::: moniker-end

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../atl/atl-com-property-pages.md)<br/>
[Ejemplos de Visual C++](../overview/visual-cpp-samples.md)
