---
title: "Actualizar un control ActiveX existente | Microsoft Docs"
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
  - "controles ActiveX [C++], Internet"
  - "CAB (archivos), para controles ActiveX"
  - "aplicaciones de Internet [C++], controles ActiveX"
  - "aplicaciones de Internet [C++], empaquetar código para descargar"
  - "otorgar licencias a controles ActiveX"
  - "archivos LPK para controles de Internet"
  - "controles OLE [C++], actualizar a ActiveX"
  - "seguro para scripting e inicialización (controles)"
  - "actualizar controles ActiveX"
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Actualizar un control ActiveX existente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controles ActiveX existentes \(antes controles OLE\) se pueden utilizar en internet sin modificaciones.  Sin embargo, puede modificar los controles para mejorar el rendimiento.  Al utilizar el control en una página Web, existen consideraciones adicionales.  El archivo .ocx y todos los archivos auxiliares deben estar en el equipo o descargar a través de Internet.  Esto crea el tamaño y el tiempo de descarga de código una consideración importante.  Descargas se pueden empaquetar en un archivo .cab firmado.  Puede marcar el control como seguro para el script, y como seguro para inicializar.  
  
 En este artículo se abordan los siguientes temas:  
  
-   [Código del paquete para descargar](#_core_packaging_code_for_downloading)  
  
-   [Marcar un Control Seguro para el script y el inicializar](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
-   [Problemas de autorización](#_core_licensing_issues)  
  
-   [Firmar el código](#_core_signing_code)  
  
-   [Administrar el Palette](#_core_managing_the_palette)  
  
-   [Niveles de Protección del explorador Internet Explorer y comportamiento de Control](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 También puede agregar optimizaciones, como se describe en [Controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md).  Monikers se pueden utilizar las propiedades de descarga y objetos binarios grandes de forma asincrónica, como se describe en [Controles ActiveX en internet](../mfc/activex-controls-on-the-internet.md).  
  
##  <a name="_core_packaging_code_for_downloading"></a> Código del paquete para descargar  
 Para obtener más información sobre este tema, vea el artículo de Knowledge Base “empaquetar Controles MFC para el uso Compilaciones internet” \(Q167158\).  Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support).  
  
### La etiqueta de CODEBASE  
 Los controles ActiveX se insertan en páginas Web mediante la etiqueta de `<OBJECT>` .  El parámetro de `CODEBASE` de la etiqueta de `<OBJECT>` especifica la ubicación de la que descargar el control.  `CODEBASE` puede notificar en varios tipos de archivo correctamente.  
  
### Mediante la etiqueta de CODEBASE con un archivo de OCX  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,70,0,1086"  
```  
  
 Esta solución sólo descargará el archivo .ocx del control, y requiere las DLL que admite que ya instalada en el equipo cliente.  Esto funcionará para Internet Explorer y los controles ActiveX de MFC compilados con Visual C\+\+, porque Internet Explorer envía con archivos DLL que admiten para controles de Visual C\+\+.  Si utilizan a otro explorador de Internet que es ActiveX CONTROL\-capaz para ver este control, esta solución no funcionará.  
  
### Mediante la etiqueta de CODEBASE con un archivo de los INF  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 Un archivo de .inf controlará la instalación de un archivo .ocx y sus archivos auxiliares.  Este método no se recomienda porque no es posible firmar un archivo de .inf \(vea [Firmar el código](#_core_signing_code) para punteros en código de firma\).  
  
### Mediante la etiqueta de CODEBASE con un archivo CAB  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,2,0,0"  
```  
  
 Los archivador. son la forma recomendada a los controles ActiveX que utilizan MFC.  Empaquetar un control ActiveX de MFC en un archivador. permite que un archivo de .inf se incluye para controlar la instalación de control ActiveX y cualquier archivo DLL dependiente \(como los archivos DLL de MFC\).  Mediante un archivo CAB automáticamente comprime el código para una descarga más rápida.  Si utiliza un archivo .cab para la descarga de componentes, es más rápido firmar el archivo .cab completo que cada componente individual.  
  
### Crear archivos CAB  
 Puede descargar el kit de desarrollo de archivador. del artículo de Knowledge [310618: Kit de desarrollo de software de archivador. de Microsoft](http://go.microsoft.com/fwlink/?LinkId=148204)Base.  En este kit encontrará las herramientas necesarias para construir los archivador.  
  
 El archivador. indicada por `CODEBASE` debe contener el archivo .ocx para el control ActiveX y un archivo de .inf para controlar la instalación.  Crea el archivador. especificando el nombre del archivo de control y un archivo de .inf.  No incluya archivos DLL dependientes que pueden existir en el sistema en este archivador.  Por ejemplo, los archivos DLL de MFC se empaquetan en un archivador. independiente y se les hace referencia por el archivo de .inf que controla.  
  
 Para obtener información sobre cómo crear un archivo CAB, vea [Crear un archivo CAB](http://msdn.microsoft.com/es-es/cc52fd09-bdf6-4410-a693-149a308f36a3).  
  
### El archivo de los INF  
 El ejemplo siguiente, spindial.inf, listas los archivos auxiliares y la información de versión necesarios para el control MFC Spindial.  Observe la ubicación de los archivos DLL de MFC es un sitio web de Microsoft.  El mfc42.cab proporcionado y firmado por Microsoft.  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,0,4261,0  
[Mfc42.dll] - FileVersion=6,0,8168,0  
[Msvcrt.dll] - FileVersion=6,0,8168,0  
```  
  
### \<La etiqueta OBJECT\>  
 El ejemplo siguiente se muestra cómo utilizar la etiqueta de `<OBJECT>` empaquetar el control de ejemplo de MFC Spindial.  
  
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
  
 En este caso, spindial.cab contendrá dos archivos, spindial.ocx y spindial.inf.  El comando siguiente compilará el archivador.:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 El parámetro de `–s 6144` reserva espacio en el archivo. CAB para la firma de código.  
  
### La etiqueta de versión  
 Observe aquí que la información de `#Version` especificada con un archivo CAB aplica al control especificado por el parámetro de `CLASSID` de la etiqueta de `<OBJECT>` .  
  
 Dependiendo de la versión especificada, puede forzar la descarga del control.  Para las especificaciones completadas de la etiqueta de `OBJECT` como el parámetro de `CODEBASE` , vea referencia de W3C.  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Marcar un Control Seguro para el script y el inicializar  
 Los controles ActiveX utilizados en páginas Web deben marcarse como safe para el script y seguro para inicializar si son de hecho seguros.  Un control seguro no realizará el disco E\/S ni tendrá acceso a la memoria o los registros de un equipo directamente.  
  
 Los Controles se pueden marcar como safe para el script y seguro para inicializar a través del registro.  Modifique `DllRegisterServer` para agregar las entradas similares a la siguiente para marcar el control como seguro para el script y la persistencia en el registro.  Un método alternativo es implementar `IObjectSafety`.  
  
 Definirá GUID \(identificadores únicos globales\) para el control para marcarlo seguro para el script y para persistencia.  Los Controles que pueden ser segura con guiones contendrán una entrada de Registro similar al siguiente:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Los Controles que se pueden inicializar con seguridad de datos persistentes son seguros marcada para persistencia con una entrada de Registro similar a:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Agregue las entradas similares al siguiente \(sustituyendo el identificador de la clase de control en lugar de `{06889605-B8D0-101A-91F1-00608CEAD5B3}`\) para asociar claves con el siguiente identificador de la clase:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> Problemas de autorización  
 Si desea utilizar un control con licencia en una página Web, debe comprobar que el contrato de licencia permite su uso en internet y crea un archivo de paquete de licencia \(LPK\) para él.  
  
 Un control ActiveX con licencia no cargará correctamente en una página HTML si el equipo que ejecuta Internet Explorer no está autorizado para utilizar el control.  Por ejemplo, si un control con licencia se compiló con Visual C\+\+, la página HTML mediante el control cargará correctamente en el equipo en que el control se compiló, pero no cargará en otro equipo a menos que la información de autorización se incluya.  
  
 Para utilizar un control ActiveX con licencia en Internet Explorer, debe comprobar el contrato de licencia del proveedor para comprobar que la licencia para el control permite:  
  
-   Redistribución  
  
-   Uso del control en internet  
  
-   Uso del parámetro de código base  
  
 Para utilizar un control con licencia en una página HTML en un equipo nonlicensed, debe generar un archivo de paquete de licencia \(LPK\).  El archivo de LPK contiene las licencias en tiempo de ejecución para los controles con licencia en la página HTML.  Este archivo se genera mediante LPK\_TOOL.EXE que se incluye en ActiveX SDK.  Para obtener más información, vea el sitio web de MSDN en [http:\/\/msdn.microsoft.com](http://msdn.microsoft.com).  
  
#### Para crear un archivo LPK  
  
1.  Ejecute LPK\_TOOL.EXE en un equipo que está autorizado para utilizar el control.  
  
2.  En el cuadro de diálogo de **License Package Authoring Tool** , en el cuadro de lista de **DisponibleControles** , seleccione cada control ActiveX con licencia que se utilizará en la página HTML y haga clic en **Add**.  
  
3.  Haga clic en **Save & Exit** y escriba un nombre para el archivo de LPK.  Esto creará el archivo de LPK y se cierra la aplicación.  
  
#### Para insertar un control con licencia en una página HTML  
  
1.  Edite la página HTML.  En la página HTML, inserte \<una etiqueta de\> objeto para el objeto de administrador de licencias antes de cualquier otra \<etiqueta\> OBJECT.  El administrador de licencias es un control ActiveX que se instala con Internet Explorer.  El identificador de la clase se muestra a continuación.  Establezca la propiedad de LPKPath del objeto de administrador de licencias en la ruta de acceso y nombre de archivo de LPK.  Puede tener sólo un archivo de LPK por la página HTML.  
  
    ```  
    <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
    </OBJECT>  
    ```  
  
2.  Inserte \<la etiqueta OBJECT\> para el control con licencia después de la etiqueta del administrador de licencias.  
  
     Por ejemplo, una página HTML que muestra el control de edición Microsoft Masked se muestra a continuación.  Identificador de la primera clase es para el control de administrador de licencias, la segunda clase que el identificador es para el control de edición Masked.  Cambie las etiquetas para señalar a la ruta de acceso relativa del archivo de .lpk que creó anteriormente, y agregue una etiqueta de objeto incluido el identificador de clase para el control.  
  
3.  Inserte \<el atributo\> de la INCRUSTACIÓN para el archivo de LPK, si usa el complemento de NCompass ActiveX.  
  
     Si el control se puede ver en otros exploradores habilitado activo \(por ejemplo, Netscape mediante el complemento de NCompass ActiveX — debe agregar \<la sintaxis\> de la INCRUSTACIÓN como se muestra a continuación.  
  
    ```  
    <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
  
        <EMBED SRC = "maskedit.LPK">  
  
    </OBJECT>  
    <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
    </OBJECT>  
    ```  
  
 Para obtener más información sobre el control que autoriza, vea [Controles ActiveX: Autorización de un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
##  <a name="_core_signing_code"></a> Firmar el código  
 La firma de código está diseñado para identificar el origen del código, y para garantizar que el código no ha cambiado desde que se firmó.  Dependiendo de la configuración de seguridad del explorador, los usuarios se advertidos antes de descargar el código.  Los usuarios pueden elegir para confiar en ciertos propietarios o compañías de certificado, en cuyo caso el código firmado por los datos es descargado sin advertencia.  El código se firma digitalmente para evitar modificaciones.  
  
 Asegúrese de que el código final se firmen para poder automáticamente descargar el control sin mostrar mensajes de advertencia de confianza.  Para obtener información sobre cómo firmar código, compruebe la documentación en Authenticode en ActiveX SDK y vea [Firmar un archivo CAB](http://msdn.microsoft.com/es-es/04d8b47a-8f1c-4b54-ab90-730fcdc03747).  
  
 Dependiendo de la configuración del nivel de confianza y la seguridad del explorador, un certificado se puede mostrar para identificar la persona o la compañía de firma.  Si el nivel de seguridad no es none, o si el propietario firmado del certificado del control es de confianza, un certificado no se mostrará.  Vea [Niveles de Protección del explorador Internet Explorer y comportamiento de Control](#_core_internet_explorer_browser_safety_levels_and_control_behavior) para obtener detalles sobre cómo la configuración de seguridad del explorador determinará si el control está descargado y un certificado se muestra.  
  
 El código de las garantías de la firma digital no ha cambiado desde que se ha firmado.  Un hash del código se extrae y se inserta en el certificado.  Este hash es más adelante en comparación con un valor hash del código tomado después de descargar el código pero antes de que se ejecuta.  Las compañías como Verisign pueden proporcionar private y las claves públicas necesarios para firmar el código.  ActiveX SDK envía con MakeCert, una utilidad para crear los certificados de prueba.  
  
##  <a name="_core_managing_the_palette"></a> Administrar el Palette  
 Los contenedores determinan la paleta y la disponibles como propiedad de ambiente, **DISPID\_AMBIENT\_PALETTE**.  Un contenedor \(por ejemplo, Internet Explorer\) elija una paleta que sea utilizada por todos los controles ActiveX en una página para determinar su propia paleta.  Esto evita que se muestre el parpadeo y muestra un aspecto coherente.  
  
 Un control puede reemplazar `OnAmbientPropertyChange` para controlar la notificación de cambios en la paleta.  
  
 Un control puede reemplazar `OnGetColorSet` para devolver un conjunto de colores para dibujar la paleta.  Los contenedores utilizan el valor devuelto para determinar si un control se paleta\- monitores.  
  
 En OCX 96 instrucciones, un control debe realizar siempre la paleta en segundo plano.  
  
 Contenedores más antiguos que no utilizan la propiedad de ambiente de la paleta se incluirán `WM_QUERYNEWPALETTE` y los mensajes de `WM_PALETTECHANGED` .  Un control puede reemplazar `OnQueryNewPalette` y `OnPaletteChanged` para administrar estos mensajes.  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Niveles de Protección del explorador Internet Explorer y comportamiento de Control  
 Un explorador tiene opciones para el nivel de seguridad, configurables por el usuario.  Como las páginas Web pueden incluir contenido activo que podría potencialmente dañar el equipo de un usuario, exploradores permiten al usuario a seleccionar las opciones del nivel de seguridad.  Según la forma un explorador implementa niveles de seguridad, el control no se puede descargar en absoluto, o mostrará un certificado o un mensaje de advertencia para permitir que el usuario elija en tiempo de ejecución si descargar el control.  El comportamiento de los controles ActiveX en alto, medio, y niveles de seguridad baja en Internet Explorer se muestra a continuación.  
  
### Modo de seguridad alta  
  
-   Los controles sin signo no se descargarán.  
  
-   Los controles firmados mostrarán un certificado si es que no es de confianza \(un usuario puede elegir una opción de confirmar siempre código de este propietario del certificado de ahora en adelante\).  
  
-   Sólo los controles marcados como seguro tendrán datos persistentes o eran que admite scripts.  
  
### Entre el modo de seguridad  
  
-   Los controles sin signo mostrarán una advertencia antes de descargar.  
  
-   Los controles firmados mostrarán un certificado si es que no es de confianza.  
  
-   Los Controles no marcadas como seguro mostrará una advertencia.  
  
### Modo de seguridad baja  
  
-   Los Controles se descargan sin advertencia.  
  
-   El script y la persistencia aparecen sin advertencia.  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)   
 [Controles ActiveX MFC: Licencias de un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)