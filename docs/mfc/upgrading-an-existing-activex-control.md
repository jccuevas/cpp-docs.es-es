---
title: Actualizar un Control ActiveX existente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e40240367d3e8350cee030b2c08dc5a48325e05f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="upgrading-an-existing-activex-control"></a>Actualizar un control ActiveX existente
Controles ActiveX existente (antes controles OLE) puede utilizarse en Internet sin modificaciones. Sin embargo, puede modificar los controles para mejorar su rendimiento. Cuando se utiliza el control en una página Web, existen consideraciones adicionales. El archivo .ocx y todos los archivos auxiliares deben estar en el equipo de destino o descargarse a través de Internet. Esto hace que el tamaño del código y una consideración importante de tiempo de descarga. Descargas se pueden empaquetar en un archivo .cab firmado. Puede marcar el control como seguros para scripting así como para inicializar.  
  
 En este artículo se trata los temas siguientes:  
  
- [Empaquetar código para su descarga](#_core_packaging_code_for_downloading)  
  
- [Marcar un Control como seguro para Scripting e inicialización](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [Problemas de licencias](#_core_licensing_issues)  
  
- [Firma de código](#_core_signing_code)  
  
- [Administrar la paleta](#_core_managing_the_palette)  
  
- [Niveles de seguridad del explorador de Internet Explorer y el comportamiento de Control](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 También puede agregar las optimizaciones, como se describe en [controles ActiveX: optimización](../mfc/mfc-activex-controls-optimization.md). Monikers pueden usarse para propiedades de descarga y BLOB de manera asincrónica, como se describe en [controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md).  
  
##  <a name="_core_packaging_code_for_downloading"></a> Empaquetar código para su descarga  
 Para obtener más información sobre este tema, vea el artículo de Knowledge Base "Empaquetado MFC controles para Use Over the Internet" (Q167158). Encontrará artículos de Knowledge Base en [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
### <a name="the-codebase-tag"></a>La etiqueta CODEBASE  
 Controles ActiveX se incrustan en páginas Web mediante la `<OBJECT>` etiqueta. El `CODEBASE` parámetro de la `<OBJECT>` etiqueta Especifica la ubicación desde la que se va a descargar el control. `CODEBASE` puede apuntar a un número de distintos tipos de archivos correctamente.  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Utilizar la etiqueta CODEBASE con un archivo OCX  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 Esta solución sólo descarga del control .ocx archivo y requiere que los archivos DLL auxiliares ya estén instalados en el equipo cliente. Esto funcionará para los controles de Internet Explorer y ActiveX de MFC compilados con Visual C++, ya que Internet Explorer se incluye con los archivos DLL auxiliares para los controles de Visual C++. Si otro explorador de Internet que sea compatible con el control ActiveX se utiliza para ver este control, esta solución no funcionará.  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>Utilizar la etiqueta CODEBASE con un archivo INF.  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 Un archivo .inf controlará la instalación del archivo .ocx y sus archivos auxiliares. Este método no se recomienda porque no es posible firmar un archivo .inf (vea [firma de código](#_core_signing_code) para punteros de firma de código).  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>Utilizar la etiqueta CODEBASE con un archivo .cab  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 Archivos contenedores son la forma recomendada para empaquetar controles ActiveX que utiliza MFC. Empaquetar un control ActiveX de MFC en un archivo .cab permite que un archivo .inf que debe incluirse para controlar la instalación del control ActiveX y cualquier DLL dependientes (como las DLL de MFC). Mediante el archivo .cab automáticamente comprime el código para agilizar la descarga. Si está utilizando un archivo .cab de descarga de componentes, es más rápido firmar el archivo .cab completo que cada componente individual.  
  
### <a name="creating-cab-files"></a>Creación de archivos CAB  
 Puede descargar el Kit de desarrollo desde el artículo de Knowledge Base [310618: Kit de desarrollo de Software de Microsoft archivador](http://go.microsoft.com/fwlink/p/?linkid=148204). En este kit encontrará las herramientas necesarias para crear archivos CAB.  
  
 El archivo .cab que señala `CODEBASE` debe contener el archivo .ocx para el control ActiveX y un archivo .inf para controlar su instalación. Crear el archivo .cab especificando el nombre de archivo del control y un archivo .inf. No incluya archivos DLL dependientes que puedan existir en el sistema en este archivo contenedor. Por ejemplo, los archivos DLL de MFC están empaquetadas en un archivo .cab independiente y que hace referencia el archivo .inf del control.  
  
 Para obtener más información sobre cómo crear un archivo .cab, consulte [crear un archivo CAB](http://msdn.microsoft.com/en-us/cc52fd09-bdf6-4410-a693-149a308f36a3).  
  
### <a name="the-inf-file"></a>El archivo INF  
 El siguiente ejemplo, spindial.inf, listas de los archivos de compatibilidad y la información de versión necesitan Spindial de MFC controlar. Tenga en cuenta que la ubicación de los archivos DLL de MFC es un sitio Web de Microsoft. El mfc42.cab se proporciona y firmados por Microsoft.  
  
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
 En el ejemplo siguiente se muestra cómo utilizar la `<OBJECT>` etiqueta para empaquetar el control de ejemplo Spindial de MFC.  
  
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
  
 En este caso, spindial.cab contiene dos archivos, spindial.ocx y spindial.inf. El comando siguiente genera el archivo .cab:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 El `-s 6144` parámetro reserva espacio en el archivo CAB para la firma de código.  
  
### <a name="the-version-tag"></a>La etiqueta de versión  
 Tenga en cuenta aquí que el `#Version` información especificada con un archivo CAB se aplica al control especificado por la `CLASSID` parámetro de la `<OBJECT>` etiqueta.  
  
 Dependiendo de la versión especificada, puede forzar la descarga del control. Para obtener la especificación completa de la `OBJECT` etiqueta incluida la `CODEBASE` parámetro, consulte el W3C la referencia.  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Marcar un Control como seguro para Scripting e inicialización  
 Controles ActiveX usados en páginas Web deben marcarse como seguros para scripting y seguro para la inicialización si de hecho sean seguros. Un control seguro no realizar E/S de disco ni tener acceso a la memoria o los registros de una máquina directamente.  
  
 Los controles pueden marcarse como seguros para scripting e inicializar mediante el registro. Modificar `DllRegisterServer` para agregar entradas similares a las siguientes opciones para marcar el control como seguros para scripting y persistencia en el registro. Un método alternativo consiste en implementar `IObjectSafety`.  
  
 Definirá globalmente identificadores únicos (GUID) para que el control de marcarlo como seguro para scripting y persistencia. Controles que pueden incluirse en scripts con seguridad contendrá una entrada del Registro similar al siguiente:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Controles que se pueden inicializar de forma segura desde datos persistentes están marcados como seguros para la persistencia con una entrada del Registro similar al:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Agregar entradas similares a lo siguiente (sustituyendo el control Id. en lugar de la clase `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) para asociar las claves con el Id. de clase siguiente:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> Problemas de licencias  
 Si desea usar un control con licencia en una página Web, debe comprobar que el contrato de licencia permite su uso en Internet y crear un archivo de paquete de licencia (LPK) para ella.  
  
 Un control ActiveX con licencia no se cargará correctamente en una página HTML si el equipo que ejecuta Internet Explorer no tiene licencia para utilizar el control. Por ejemplo, si un control con licencia se generó con Visual C++, la página HTML mediante el control se cargará correctamente en el equipo donde se creó el control, pero no se cargará en un equipo diferente, a menos que se incluye información de licencia.  
  
 Para usar un control ActiveX con licencia en Internet Explorer, debe comprobar el contrato de licencia del proveedor para comprobar que la licencia para el control permite:  
  
-   Redistribución  
  
-   Uso del control de Internet  
  
-   Uso del parámetro Codebase  
  
 Para usar un control con licencia en una página HTML abierta en un equipo, debe generar un archivo de paquete de licencia (LPK). El archivo LPK contiene licencias de tiempo de ejecución para los controles con licencia en la página HTML. Este archivo se genera a través de LPK_TOOL. EXE que se incluye con el SDK de ActiveX. Para obtener más información, vea el sitio Web de MSDN en [ http://msdn.microsoft.com ](http://msdn.microsoft.com).  
  
#### <a name="to-create-an-lpk-file"></a>Para crear un archivo LPK  
  
1.  Ejecute LPK_TOOL. EXE en un equipo que tiene licencia para utilizar el control.  
  
2.  En el **License Package Authoring Tool** cuadro de diálogo, en la **controles disponibles** cuadro de lista, seleccione cada licencia control ActiveX que se usará en la página HTML y haga clic en **agregar**.  
  
3.  Haga clic en **guardar y salir** y escriba un nombre para el archivo LPK. Esto creará el archivo LPK y cierre la aplicación.  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Para incrustar un control con licencia en una página HTML  
  
1.  Edite la página HTML. En la página HTML, inserte una \<objeto > etiqueta para el objeto de administrador de licencias antes que cualquier otro \<objeto > etiquetas. El Administrador de licencias es un control ActiveX que se instala con Internet Explorer. A continuación se muestra su Id. de clase. Establezca la propiedad LPKPath del objeto License Manager para la ruta de acceso y el nombre del archivo LPK. Puede tener solo un archivo LPK por página HTML.  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  Insertar el \<objeto > etiqueta para el control con licencia después de la etiqueta del Administrador de licencias.  
  
     Por ejemplo, a continuación se muestra una página HTML que muestra el control Masked Edit de Microsoft. La primera clase que identificador es para el control del Administrador de licencias, la clase de segundo que identificador es para el control de edición enmascarado. Cambiar las etiquetas para que apunte a la ruta de acceso relativa del archivo LPK que creó anteriormente y agregue una etiqueta de objeto incluidos el identificador de clase para el control.  
  
3.  Insertar el \<Insertar > atributo para el archivo LPK, si usa el complemento NCompass ActiveX.  
  
     Si el control puede verse en otro activo exploradores compatibles: por ejemplo, Netscape mediante el complemento NCompass ActiveX, debe agregar el \<Insertar > sintaxis, tal como se muestra a continuación.  
  
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
 Firma de código está diseñada para identificar el origen del código y garantizar que el código no ha cambiado desde que se firmó. Dependiendo de la configuración de seguridad del explorador, pueden advertir a los usuarios antes de descarga el código. Los usuarios pueden elegir confiar en ciertos propietarios de certificados o empresas, en los cuales caso el código firmado en función de confianza se descargará sin previo aviso. Código está firmado digitalmente para evitar alteraciones.  
  
 Asegúrese de que el código final está firmado de manera que el control se puede descargar automáticamente sin mostrar mensajes de advertencia de confianza. Para obtener más información sobre cómo firmar código, consulte la documentación de Authenticode en ActiveX SDK y vea [firmar un archivo CAB](http://msdn.microsoft.com/en-us/04d8b47a-8f1c-4b54-ab90-730fcdc03747).  
  
 Según la configuración de nivel seguridad de confianza y el explorador, puede mostrarse un certificado para identificar la persona o empresa. Si el nivel de seguridad es none, o si el propietario del certificado firmado del control es de confianza, no se mostrará un certificado. Vea [niveles de seguridad del explorador de Internet Explorer y controlar el comportamiento](#_core_internet_explorer_browser_safety_levels_and_control_behavior) para obtener más información sobre cómo la configuración de seguridad del explorador determinan si el control se descarga y muestra un certificado.  
  
 Código de garantías de la firma digital no ha cambiado desde que se firmó. Un hash del código y se incrusta en el certificado. Este hash más adelante se compara con un valor hash del código que realiza una vez descargado el código pero antes de ejecutarlo. Compañías como Verisign pueden proporcionar las claves públicas y privadas necesarios para firmar el código. El SDK de ActiveX se suministra con MakeCert, una herramienta de creación de certificados de prueba.  
  
##  <a name="_core_managing_the_palette"></a> Administrar la paleta  
 Contenedores determinan la paleta y hacer que esté disponible como una propiedad de ambiente, **DISPID_AMBIENT_PALETTE**. Un contenedor (por ejemplo, Internet Explorer) elige una paleta que se usa por todos los controles ActiveX en una página para determinar su propia paleta. Esto impide el parpadeo de pantalla y no presenta un aspecto coherente.  
  
 Un control puede reemplazar `OnAmbientPropertyChange` para controlar la notificación de cambios en la paleta.  
  
 Un control puede reemplazar `OnGetColorSet` para devolver un conjunto para dibujar la paleta de colores. Contenedores utilizan el valor devuelto para determinar si un control es compatible con la paleta.  
  
 En las directrices de programación OCX 96, un control siempre debe realizar su paleta en segundo plano.  
  
 Contenedores más antiguos que no utilice la propiedad de ambiente paleta enviará `WM_QUERYNEWPALETTE` y `WM_PALETTECHANGED` mensajes. Un control puede invalidar `OnQueryNewPalette` y `OnPaletteChanged` para controlar estos mensajes.  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Niveles de seguridad del explorador de Internet Explorer y el comportamiento de Control  
 Opciones de nivel de seguridad, configurable por el usuario tiene un explorador. Dado que las páginas Web pueden contener contenido activo que podría dañar el equipo de un usuario, exploradores permiten al usuario seleccionar opciones de nivel de seguridad. Dependiendo de la forma en que un explorador implementa los niveles de seguridad, un control no se puede descargar en absoluto, o mostrará un certificado o un mensaje de advertencia para permitir al usuario elegir en tiempo de ejecución si desea descargar el control o no. A continuación se enumera el comportamiento de los controles ActiveX en niveles de seguridad alta, Media y baja en Internet Explorer.  
  
### <a name="high-safety-mode"></a>Modo de alta seguridad  
  
-   No se descargan los controles sin firmar.  
  
-   Los controles firmados mostrarán un certificado si no es de confianza (un usuario puede elegir una opción para confiar siempre en el código de este propietario del certificado de ahora en adelante).  
  
-   Solo los controles marcados como seguros se tienen datos persistentes o ser convertible en scripts.  
  
### <a name="medium-safety-mode"></a>Modo de seguridad Media:  
  
-   Los controles no firmados mostrarán una advertencia antes de descargar.  
  
-   Los controles firmados mostrarán un certificado si no es de confianza.  
  
-   Los controles no marcados como seguros mostrará una advertencia.  
  
### <a name="low-safety-mode"></a>Modo de seguridad baja  
  
-   Los controles se descargan sin previo aviso.  
  
-   Secuencias de comandos y persistencia se producen sin previo aviso.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Conceptos básicos de programación de Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Controles ActiveX MFC: Licencias de un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

