---
title: "Example: Implementing a Property Page | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "páginas de propiedades, implementar"
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Example: Implementing a Property Page
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo compilar una página de propiedades que muestre \(y permite cambiar\) las propiedades de la interfaz de [Clases de documento](../mfc/document-classes.md) .  Esta interfaz es expuesta por los documentos en [Ejemplos del modelo de objetos de entorno común](../Topic/Common%20Environment%20Object%20Model%20Examples.md) de Visual Studio \(aunque la página de propiedades que creará no cuidará de donde los objetos que manipulan alcanzado mientras admiten la interfaz correcta\).  
  
 el ejemplo se basa en [Ejemplo ATLPages](../top/visual-cpp-samples.md).  
  
 Para completar este ejemplo, debe:  
  
-   [Agregue la clase de la página de propiedades ATL](#vcconusing_the_atl_object_wizard) mediante el cuadro de diálogo agregar clase y el Asistente para páginas de propiedades ATL.  
  
-   [Edite el recurso de cuadro de diálogo](#vcconediting_the_dialog_resource) agregando nuevos controles para las propiedades interesantes de la interfaz de **Documento** .  
  
-   [Agregue controladores de mensajes](#vcconadding_message_handlers) para mantener el sitio de la página de propiedades a los cambios realizados por el usuario.  
  
-   Agregue algunas instrucciones de `#import` y una definición en la sección de [mantenimiento](#vcconhousekeeping) .  
  
-   [Reemplazo IPropertyPageImpl:: SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) para validar los objetos que se pasan a la página de propiedades.  
  
-   [Reemplazo IPropertyPageImpl:: Activar](#vcconoverriding_ipropertypageimpl_activate) para inicializar la interfaz de la página de propiedades.  
  
-   [Reemplazo IPropertyPageImpl:: Aplicar](#vcconoverride_ipropertypageimpl_apply) para actualizar el objeto con los últimos valores de propiedad.  
  
-   [Abra la página de propiedades](#vccontesting_the_property_page) creando un objeto simple auxiliares.  
  
-   [cree una macro](#vcconcreating_a_macro) que va a la página de propiedades.  
  
##  <a name="vcconusing_the_atl_object_wizard"></a> Agregar una clase de la página de propiedades ATL  
 Primero, cree un nuevo proyecto ATL para un servidor de una DLL denominada `ATLPages7`.  ahora utilice [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) para generar una página de propiedades.  Dé a la página de propiedades **nombre corto** de **DocProperties** después a **Cadenas** la página para establecer elementos propiedad\-página\-específicos tal y como se muestra en la siguiente tabla.  
  
|Elemento|Valor|  
|--------------|-----------|  
|Título|TextDocument|  
|Cadena de Documento|propiedades de VCUE TextDocument|  
|Helpfile|*\<espacio en blanco\>*|  
  
 Los valores que establece en esta página del asistente devolverán al contenedor de la página de propiedades cuando llama a **IPropertyPage:: GetPageInfo**.  Lo que sucede con las cadenas después que depende del contenedor, pero se utilizan normalmente para identificar la página al usuario.  El título aparecerá normalmente en una ficha a la página y la cadena de Documento se puede mostrar en una barra de estado o una información sobre herramientas \(aunque el cuadro estándar de la propiedad no utiliza esta cadena en absoluto\).  
  
> [!NOTE]
>  Las cadenas que el asistente establece aquí almacena como recursos de cadena en el proyecto.  Es fácil modificar estas cadenas utilizando el editor de recursos si necesita cambiar esta información después del código de la página se ha generado.  
  
 Haga clic **Aceptar** para que el asistente genere la página de propiedades.  
  
##  <a name="vcconediting_the_dialog_resource"></a> Editar el recurso de cuadro de diálogo  
 Ahora que se ha generado la página de propiedades, necesitará agregar controles al recurso de cuadro de diálogo que representa la página.  Agregue un cuadro de edición, un control de texto estático, y una casilla y establezca su id. como se muestra a continuación:  
  
 ![Edición de un recurso de cuadro de diálogo](../atl/media/ppgresourcelabeled.png "PPGResourceLabeled")  
  
 Estos controles se utilicen para mostrar el nombre de archivo de documento y su estado de sólo lectura.  
  
> [!NOTE]
>  El recurso de cuadro de diálogo no incluye un marco o los botones de comando, ni tampoco tabular tengan que puede haber esperado.  Estas características son proporcionadas por un marco de página de propiedades como el que se creó llamando a [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437).  
  
##  <a name="vcconadding_message_handlers"></a> Controladores de mensajes de suma  
 Con el nombre de los controles, puede agregar controladores de mensajes para actualizar el estado modificado de la página cuando el valor de cualquiera de los cambios de controles:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/CPP/example-implementing-a-property-page_1.h)]  
  
 Este código responde a los cambios realizados en el control de edición o la casilla llamando a [IPropertyPageImpl:: SetDirty](../Topic/IPropertyPageImpl::SetDirty.md), que informa al sitio de la página que la página ha cambiado.  El sitio de la página responderá normalmente habilitar o deshabilitar un botón de **Aplicar** en el cuadro de la página de propiedades.  
  
> [!NOTE]
>  En poseer las páginas de propiedades, puede ser necesario realizar un seguimiento de exacto que las propiedades han sido modificadas por el usuario para poder impedir actualizar las propiedades que no se han cambiado.  Este ejemplo aplica ese código un seguimiento de los valores de propiedad originales y comparándolos con los valores actuales de la interfaz de usuario cuando llega el momento de aplicar los cambios.  
  
##  <a name="vcconhousekeeping"></a> mantenimiento  
 Ahora agregue un par de instrucciones de `#import` a DocProperties.h de modo que el compilador sepa sobre la interfaz de **Documento** :  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/CPP/example-implementing-a-property-page_2.h)]  
  
 También necesitará hacer referencia a la clase base de `IPropertyPageImpl` ; agregue `typedef` siguiente a la clase de **CDocProperties** :  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/CPP/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Reemplazar IPropertyPageImpl:: SetObjects  
 El primer método de `IPropertyPageImpl` que necesita invalidar es [SetObjects](../Topic/IPropertyPageImpl::SetObjects.md).  A continuación agregará código para comprobar que solo se ha pasado un objeto único y admite la interfaz de **Documento** que espera:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/CPP/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  Tiene sentido de admitir un solo objeto de esta página porque permitirá que el usuario establezca el nombre de archivo de objeto \(solo un archivo puede existir en una ubicación.  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Reemplazar IPropertyPageImpl:: Activar  
 El paso siguiente es inicializar la página de propiedades con los valores de propiedad del objeto subyacente cuando la página se crea por primera vez.  
  
 En este caso debe agregar los miembros siguientes a la clase puesto que también utilizará los valores de propiedad iniciales para la comparación cuando se aplican los usuarios de la página los cambios:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/CPP/example-implementing-a-property-page_5.h)]  
  
 La implementación de la clase base del método de [Activar](../Topic/IPropertyPageImpl::Activate.md) es responsable de crear el cuadro de diálogo y sus controles, lo que puede invalidar este método y agregarlo dispone de inicialización después de llamar a la clase base:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/CPP/example-implementing-a-property-page_6.h)]  
  
 Este código utiliza los métodos COM de la interfaz de **Documento** para obtener las propiedades de interés.  Utilice los contenedores de la API Win32 proporcionados por [CDialogImpl](../atl/reference/cdialogimpl-class.md) y sus clases base para mostrar los valores de propiedad al usuario.  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Reemplazar IPropertyPageImpl:: Aplicar  
 Cuando los usuarios desean aplicar los cambios en los objetos, el sitio de la página de propiedades llamará al método de [Aplicar](../Topic/IPropertyPageImpl::Apply.md) .  Éste es el lugar para hacer el inverso del código en **Activar** — mientras **Activar** tardó valores de objeto y los insertó en los controles de la página de propiedades, **Aplicar** toma los valores de los controles en la página de propiedades y los inserta en el objeto.  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/CPP/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  La comprobación en [m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md) al principio de esta implementación es una comprobación inicial para evitar las actualizaciones innecesarias de objetos si **Aplicar** se llama más de una vez.  Hay también comprueba en cada uno de los valores de propiedad para asegurarse de que solo los cambios da lugar a una llamada al método a **Documento**.  
  
> [!NOTE]
>  Expone **Fullname** de**Documento** como propiedad de sólo lectura.  Para actualizar el nombre de archivo de documento basado en los cambios realizados en la página de propiedades, hay que utilizar el método de **Guardar** para guardar el archivo con un nombre diferente.  Así, el código de una página de propiedades no tiene que limitarse a obtener o establecer propiedades.  
  
##  <a name="vccontesting_the_property_page"></a> Mostrar la página de propiedades  
 Para mostrar esta página, debe crear un objeto simple auxiliares.  El objeto auxiliar proporcionará un método que simplifica **OleCreatePropertyFrame** API para mostrar una única página conectada a un único objeto.  Esta aplicación auxiliar se diseñó para que se pueda utilizar de Visual Basic.  
  
 Utilice [agregue el cuadro de diálogo de la clase](../ide/add-class-dialog-box.md) y [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md) para generar una nueva clase y utilizar `Helper` como su nombre corto.  Una vez creado, agregue un método como se muestra en la siguiente tabla.  
  
|Elemento|Valor|  
|--------------|-----------|  
|Nombre del método|`ShowPage`|  
|Parámetros|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 El parámetro de `bstrCaption` es la leyenda que se mostrará como título del cuadro de diálogo.  El parámetro de `bstrID` es una cadena que representa el CLSID o ProgID de la página de propiedades para mostrar.  El parámetro de `pUnk` será el puntero de `IUnknown` de objeto cuyas propiedades se configurarán por la página de propiedades.  
  
 Implemente el método como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/CPP/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a> crear una macro  
 Una vez compilado el proyecto, puede probar la página de propiedades y el objeto auxiliar mediante una macro simple que puede crear y ejecutar en el entorno de desarrollo de Visual Studio.  Esta macro creará un objeto auxiliar, después llama a su método de **ShowPage** mediante ProgID de la página de propiedades de **DocProperties** y el puntero de **IUnknown** de documento activo actualmente en el editor de Visual Studio.  El código que necesita para esta macro se muestra a continuación:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
  
Public Module AtlPages  
  
    Public Sub Test()  
        Dim Helper  
        Helper = CreateObject("ATLPages7.Helper.1")  
  
        On Error Resume Next  
        Helper.ShowPage( _  
            ActiveDocument.Name, _  
            "ATLPages7Lib.DocumentProperties.1", _  
            DTE.ActiveDocument _  
            )  
    End Sub  
  
End Module  
```  
  
 Al ejecutar esta macro, la página de propiedades se mostrará que muestra el nombre de archivo y el estado de sólo lectura actualmente de documento de texto activo.  El estado de sólo lectura del documento sólo refleja la capacidad para escribir el documento en el entorno de desarrollo; no afecta al atributo de sólo lectura del archivo en el disco.  
  
## Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../top/visual-cpp-samples.md)