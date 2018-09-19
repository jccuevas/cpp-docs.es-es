---
title: Actualizar un Control ActiveX existente | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bca0cca66f7f8b9c59dcea4911550abfc2024c8
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535280"
---
# <a name="upgrading-an-existing-activex-control"></a>Actualizar un control ActiveX existente
Los controles ActiveX existentes (antes controles OLE) puede usarse en Internet sin ninguna modificación. Sin embargo, puede modificar los controles para mejorar su rendimiento. 

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Cuando se usa el control en una página Web, existen consideraciones adicionales. El archivo .ocx y todos los archivos auxiliares deben estar en el equipo de destino o descargarse a través de Internet. Esto hace que el tamaño del código y descarga una consideración importante de tiempo. Las descargas se pueden empaquetar en un archivo .cab firmado. Puede marcar el control como seguros para scripting así como para inicializar.  
  
 En este artículo se trata los temas siguientes:  
  
- [Empaquetar código para su descarga](#_core_packaging_code_for_downloading)  
  
- [Marcar un Control como seguro para Scripting e inicialización](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [Problemas de licencias](#_core_licensing_issues)  
  
- [Firma de código](#_core_signing_code)  
  
- [Administración de la paleta](#_core_managing_the_palette)  
  
- [Niveles de seguridad del explorador de Internet Explorer y el comportamiento de Control](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 También puede agregar las optimizaciones, como se describe en [controles ActiveX: optimización](../mfc/mfc-activex-controls-optimization.md). Monikers pueden usarse para descargar las propiedades y el BLOB de manera asincrónica, como se describe en [controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md).  
  
##  <a name="_core_packaging_code_for_downloading"></a> Empaquetar código para su descarga  
 Para obtener más información sobre este tema, consulte el artículo de Knowledge Base "Empaquetado MFC controles de uso a través de Internet" (Q167158). Puede encontrar artículos de Knowledge Base en [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
### <a name="the-codebase-tag"></a>La etiqueta a la base de código  
 Controles ActiveX se incrustan en páginas Web mediante la `<OBJECT>` etiqueta. El `CODEBASE` parámetro de la `<OBJECT>` etiqueta Especifica la ubicación desde la que se va a descargar el control. `CODEBASE` puede apuntar a un número de tipos de archivo diferente.  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Uso de la etiqueta a la base de código con un archivo OCX  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 Esta solución sólo descarga del control OCX archivo y requiere que los archivos DLL auxiliares ya esté instalado en el equipo cliente. Esto funcionará para los controles de Internet Explorer y ActiveX de MFC creados con Visual C++, ya que Internet Explorer se incluye con los archivos DLL auxiliares para los controles de Visual C++. Si se usa otro explorador de Internet que sea compatible con el control ActiveX para ver este control, esta solución no funcionará.  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>Uso de la etiqueta a la base de código con un archivo INF  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 Un archivo .inf controlará la instalación del archivo .ocx y sus archivos auxiliares. Este método no se recomienda porque no es posible firmar un archivo .inf (consulte [firma de código](#_core_signing_code) para punteros de firma de código).  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>Uso de la etiqueta a la base de código con un archivo .cab  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 Archivos contenedores son la manera recomendada para empaquetar controles ActiveX que utiliza la biblioteca MFC. Empaquetado de un control ActiveX de MFC en un archivo .cab permite que un archivo .inf que se incluirán para controlar la instalación del control ActiveX y los archivos DLL dependientes (por ejemplo, los archivos DLL de MFC). Con un archivo CAB automáticamente comprime el código para agilizar la descarga. Si usa un archivo .cab de descarga de componentes, es más rápido firmar el archivo .cab todo que cada componente individual.  
  
### <a name="creating-cab-files"></a>Creación de archivos CAB  
 Puede descargar el Kit de desarrollo desde el artículo de Knowledge Base [310618: Kit de desarrollo de Software de Microsoft Cabinet](http://go.microsoft.com/fwlink/p/?linkid=148204). En este kit encontrará las herramientas necesarias para crear archivos CAB.  
  
 El archivo .cab que apunta `CODEBASE` debe contener el archivo .ocx para el control ActiveX y un archivo .inf para controlar su instalación. Crear el archivo contenedor especificando el nombre del archivo de control y un archivo .inf. No incluya archivos DLL dependientes que ya existan en el sistema de este archivo CAB. Por ejemplo, los archivos DLL de MFC están empaquetadas en un archivo .cab independiente y que hace referencia el archivo .inf que controla.  
  
 Para obtener más información sobre cómo crear un archivo .cab, consulte [crear un archivo CAB](/windows/desktop/devnotes/cabinet-api-functions).  
  
### <a name="the-inf-file"></a>El archivo INF  
 El siguiente ejemplo, spindial.inf, listas de los archivos auxiliares y la información de versión es necesario para el Spindial MFC control. Tenga en cuenta que la ubicación de los archivos DLL de MFC es un sitio Web de Microsoft. Proporciona el mfc42.cab y firmado por Microsoft.  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0  
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0  
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0  
```  
  
### <a name="the-object-tag"></a>La \<objeto > etiqueta  
 El ejemplo siguiente se muestra cómo utilizar el `<OBJECT>` etiqueta para empaquetar el control de ejemplo Spindial de MFC.  
  
```  
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51  
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3" 
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001"> 
 <PARAM NAME="_Version" VALUE="65536">  
 <PARAM NAME="_ExtentX" VALUE="2646">  
 <PARAM NAME="_ExtentY" VALUE="1323">  
 <PARAM NAME="_StockProps" VALUE="0">  
 <PARAM NAME="NeedlePosition" VALUE="2">  
</OBJECT>  
```  
  
 En este caso, spindial.cab contendrá dos archivos, spindial.ocx y spindial.inf. El comando siguiente genera el archivo .cab:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 El `-s 6144` parámetro reserva espacio en el archivo CAB para la firma de código.  
  
### <a name="the-version-tag"></a>La etiqueta de versión  
 Tenga en cuenta aquí que el `#Version` información especificada con un archivo CAB se aplica al control especificado por el *CLASSID* parámetro de la `<OBJECT>` etiqueta.  
  
 Dependiendo de la versión especificada, puede forzar la descarga del control. Para la especificación completa de la `OBJECT` etiqueta incluyendo el *CODEBASE* parámetro, consulte el W3C la referencia.  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Marcar un Control como seguro para Scripting e inicialización  
 Controles ActiveX utilizados en las páginas Web deben marcarse como seguros para scripting e inicializar si de hecho son seguros. Un control seguro no realizar E/S de disco ni tener acceso a la memoria o los registros de una máquina directamente.  
  
 Los controles pueden marcarse como seguros para scripting e inicializar mediante el registro. Modificar `DllRegisterServer` para agregar entradas similares a las siguientes opciones para marcar el control como seguros para scripting y la persistencia en el registro. Un método alternativo consiste en implementar `IObjectSafety`.  
  
 Definirá globalmente identificadores únicos (GUID) para que el control que va a marcar seguros para scripting y persistencia. Los controles que pueden generarse de forma segura contendrá una entrada del Registro similar al siguiente:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Controles que se pueden inicializar de forma segura desde datos persistentes están marcados como seguros para la persistencia con una entrada del Registro similar a:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Agregue entradas similares a lo siguiente (Id. en lugar de la clase sustituyendo el control `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) para asociar las claves con el identificador de clase siguiente:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> Problemas de licencias  
 Si desea usar un control con licencia en una página Web, debe comprobar que el contrato de licencia permite su uso en Internet y crear un archivo de paquete de licencia (LPK) para ella.  
  
 Un control ActiveX con licencia no se cargará correctamente en una página HTML si el equipo que ejecuta Internet Explorer no tiene licencia para usar el control. Por ejemplo, si un control con licencia se creó mediante Visual C++, la página HTML mediante el control se cargará correctamente en el equipo donde se creó el control, pero no se cargará en un equipo diferente, a menos que se incluye información de licencia.  
  
 Para usar un control ActiveX con licencia en Internet Explorer, debe comprobar el contrato de licencia del proveedor para comprobar que la licencia para el control permite:  
  
-   Redistribución  
  
-   Uso del control de Internet  
  
-   Uso del parámetro Codebase  
  
 Para usar un control con licencia en una página HTML abierta en un equipo, debe generar un archivo de paquete de licencia (LPK). El archivo LPK contiene licencias en tiempo de ejecución para los controles con licencia en la página HTML. Este archivo se genera a través de LPK_TOOL. EXE que se incluye con el SDK de ActiveX. Para obtener más información, vea el sitio Web de MSDN en [ http://msdn.microsoft.com ](http://msdn.microsoft.com).  
  
#### <a name="to-create-an-lpk-file"></a>Para crear un archivo LPK  
  
1.  Ejecute LPK_TOOL. EXE en un equipo que tiene licencia para usar el control.  
  
2.  En el **License Package Authoring Tool** cuadro de diálogo el **controles disponibles** cuadro de lista, seleccione cada control ActiveX que se usará en la página HTML y haga clic en la licencia **agregar**.  
  
3.  Haga clic en **guardar y salir** y escriba un nombre para el archivo LPK. Esto creará el archivo LPK y cierre la aplicación.  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Para incrustar un control con licencia en una página HTML  
  
1.  Edite la página HTML. En la página HTML, inserte un \<objeto > etiqueta para el objeto de administrador de licencias antes que cualquier otro \<objeto > etiquetas. El Administrador de licencias es un control ActiveX que se instala con Internet Explorer. A continuación se muestra su Id. de clase. Establezca la propiedad LPKPath del objeto License Manager para la ruta de acceso y el nombre del archivo LPK. Puede tener un solo archivo LPK por página HTML.  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  Insertar el \<objeto > etiqueta para el control con licencia después de la etiqueta del Administrador de licencias.  
  
     Por ejemplo, a continuación se muestra una página HTML que muestra el control de edición enmascarada de Microsoft. La primera clase que es el identificador para el control del Administrador de licencias, la segunda clase que es el identificador para el control de edición enmascarado. Cambiar las etiquetas para que apunte a la ruta de acceso relativa del archivo LPK que creó anteriormente y agregue una etiqueta de objeto, incluidos el identificador de clase para el control.  
  
3.  Insertar el \<Insertar > atributo para el archivo LPK, si usa el complemento NCompass ActiveX.  
  
     Si el control puede verse en otros activo exploradores compatibles, por ejemplo, Netscape mediante el complemento NCompass ActiveX, debe agregar el \<EMBED > sintaxis, tal como se muestra a continuación.  
  
 ```  
 <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
 
 <EMBED SRC = "maskedit.LPK">  
 
 </OBJECT>  
 <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
 </OBJECT>  
 ```  
  
 Para obtener más información acerca de las licencias de control, vea [controles ActiveX: licencias de un ActiveX Control](../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
##  <a name="_core_signing_code"></a> Firma de código  
 Firma de código está diseñada para identificar el origen del código y garantizar que el código no ha cambiado desde que se firmó. Según la configuración de seguridad del explorador, es posible que se advierte a los usuarios antes de descarga el código. Los usuarios pueden decidir confiar en determinados los propietarios de certificados o las empresas, en el que caso firmado por los que el código de confianza se descargará sin previo aviso. Código está firmado digitalmente para evitar alteraciones.  
  
 Asegúrese de que se firma el código final para que el control puede descargarse automáticamente sin mostrar mensajes de advertencia de confianza. Para obtener más información sobre cómo firmar el código, consulte la documentación de Authenticode en ActiveX SDK y consulte [firmar un archivo CAB](/windows/desktop/devnotes/cabinet-api-functions).  
  
 Según la configuración del nivel seguridad de confianza y el explorador, puede mostrarse un certificado para identificar la persona o empresa. Si el nivel de seguridad es none, o si el propietario del certificado firmado del control es de confianza, no se mostrará un certificado. Consulte [niveles de seguridad del explorador de Internet Explorer y controlar el comportamiento de](#_core_internet_explorer_browser_safety_levels_and_control_behavior) para obtener más información sobre cómo la configuración de seguridad del explorador determinará si se descarga el control y un certificado que se muestra.  
  
 Código de garantías de firma digital no ha cambiado desde que se firmó. Un valor hash del código y se incrusta en el certificado. Este hash más adelante se compara con un hash del código tomado una vez descargado el código, pero antes de ejecutarlo. Las empresas, como Verisign pueden proporcionar claves públicas y privadas, es necesarias para firmar el código. El SDK de ActiveX se suministra con MakeCert, una herramienta de creación de certificados de prueba.  
  
##  <a name="_core_managing_the_palette"></a> Administración de la paleta  
 Contenedores determinan la paleta y que esté disponible como una propiedad de ambiente, **DISPID_AMBIENT_PALETTE**. Un contenedor (por ejemplo, Internet Explorer) elige una paleta que se usa por todos los controles ActiveX en una página para determinar su propia paleta. Esto evita el parpadeo de pantalla y presenta una apariencia coherente.  
  
 Un control puede invalidar `OnAmbientPropertyChange` para controlar la notificación de cambios en la paleta.  
  
 Un control puede invalidar `OnGetColorSet` para devolver un conjunto para dibujar la paleta de colores. Contenedores usan el valor devuelto para determinar si un control es compatible con la paleta.  
  
 Según las directrices de OCX 96, un control siempre debe tener en cuenta su paleta en segundo plano.  
  
 Contenedores más antiguos que no usen la propiedad de ambiente paleta enviará mensajes WM_QUERYNEWPALETTE y WM_PALETTECHANGED. Un control puede invalidar `OnQueryNewPalette` y `OnPaletteChanged` para controlar estos mensajes.  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Niveles de seguridad del explorador de Internet Explorer y el comportamiento de Control  
 Un explorador tiene opciones para el nivel de seguridad, configurable por el usuario. Dado que las páginas Web puede contener contenido activo que podría dañar el equipo de un usuario, los exploradores permiten al usuario seleccionar opciones de nivel de seguridad. Según la manera en que un explorador implementa los niveles de seguridad, un control no se puede descargar en absoluto, o mostrará un certificado o un mensaje de advertencia para permitir al usuario elegir en tiempo de ejecución si se deben descargar el control. A continuación se enumeran el comportamiento de los controles de ActiveX en niveles de seguridad alta, Media y baja en Internet Explorer.  
  
### <a name="high-safety-mode"></a>Modo de alta seguridad  
  
-   No se descargan los controles sin firmar.  
  
-   Los controles firmados mostrarán un certificado si no es de confianza (un usuario puede elegir una opción para confiar siempre en el código de este propietario del certificado de ahora en adelante).  
  
-   Solo los controles marcados como seguros se datos persistentes o ser convertible en scripts.  
  
### <a name="medium-safety-mode"></a>Modo de seguridad Media  
  
-   Los controles sin firmar mostrarán una advertencia antes de descargar.  
  
-   Los controles firmados mostrarán un certificado si no es de confianza.  
  
-   Los controles no marcados como seguros mostrará una advertencia.  
  
### <a name="low-safety-mode"></a>Modo de seguridad baja  
  
-   Los controles se descargan sin previo aviso.  
  
-   Secuencias de comandos y persistencia se producen sin previo aviso.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Conceptos básicos de programación de Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Controles ActiveX MFC: Licencias de un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

