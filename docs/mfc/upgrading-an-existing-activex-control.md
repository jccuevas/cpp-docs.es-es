---
title: Actualizar un control ActiveX existente
ms.date: 09/12/2018
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
ms.openlocfilehash: dfee42369b698956f4f91ab61a1f37e0ef06d9f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754503"
---
# <a name="upgrading-an-existing-activex-control"></a>Actualizar un control ActiveX existente

Los controles ActiveX existentes (anteriormente controles OLE) se pueden usar en Internet sin modificaciones. Sin embargo, es posible que desee modificar los controles para mejorar su rendimiento.

> [!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Cuando se usa el control en una página Web, hay consideraciones adicionales. El archivo .ocx y todos los archivos auxiliares deben estar en el equipo de destino o descargarse a través de Internet. Esto hace que el tamaño del código y el tiempo de descarga sean una consideración importante. Las descargas se pueden empaquetar en un archivo .cab firmado. Puede marcar el control como seguro para secuencias de comandos y como seguro para la inicialización.

En este artículo se tratan los temas siguientes:

- [Código de embalaje para descargar](#_core_packaging_code_for_downloading)

- [Marcar un control seguro para scripting e inicializar](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Consideraciones acerca de las licencias](#_core_licensing_issues)

- [Código de firma](#_core_signing_code)

- [Gestión de la paleta](#_core_managing_the_palette)

- [Niveles de seguridad y comportamiento de control del navegador Internet Explorer](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

También puede agregar optimizaciones, como se describe en [Controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md). Los monikers se pueden utilizar para descargar propiedades y bLOB grandes de forma asincrónica, como se describe en [Controles ActiveX en Internet.](../mfc/activex-controls-on-the-internet.md)

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>Código de embalaje para descargar

Para obtener más información sobre este tema, consulte Empaquetado de [controles ActiveX](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>La etiqueta CODEBASE

Los controles ActiveX se incrustan `<OBJECT>` en páginas Web mediante la etiqueta. El `CODEBASE` parámetro `<OBJECT>` de la etiqueta especifica la ubicación desde la que se va a descargar el control. `CODEBASE`puede apuntar a varios tipos de archivos diferentes con éxito.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Uso de la etiqueta CODEBASE con un archivo OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Esta solución descarga solo el archivo .ocx del control y requiere que los archivos DLL compatibles ya estén instalados en el equipo cliente. Esto funcionará para los controles ActiveX de Internet Explorer y MFC creados con Visual C++, porque Internet Explorer incluye los archivos DLL compatibles para los controles de Visual C++. Si se utiliza otro explorador de Internet compatible con el control ActiveX para ver este control, esta solución no funcionará.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Uso de la etiqueta CODEBASE con un archivo INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Un archivo .inf controlará la instalación de un archivo .ocx y sus archivos auxiliares. Este método no se recomienda porque no es posible firmar un archivo .inf (consulte Código de [firma](#_core_signing_code) para los punteros en la firma de código).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Uso de la etiqueta CODEBASE con un archivo CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Los archivos archivadores son la forma recomendada de empaquetar controles ActiveX que usan MFC. Empaquetar un control ActiveX MFC en un archivo archivador permite incluir un archivo .inf para controlar la instalación del control ActiveX y los archivos DLL dependientes (como los archivos DLL de MFC). El uso de un archivo CAB comprime automáticamente el código para una descarga más rápida. Si utiliza un archivo .cab para la descarga de componentes, es más rápido firmar todo el archivo .cab que cada componente individual.

### <a name="creating-cab-files"></a>Creación de archivos CAB

Las herramientas para crear archivos archivadores ahora forman parte del SDK de [Windows 10.](https://dev.windows.com/downloads/windows-10-sdk)

El archivo archivador `CODEBASE` al que se apunta debe contener el archivo .ocx del control ActiveX y un archivo .inf para controlar su instalación. Puede crear el archivo archivador especificando el nombre del archivo de control y un archivo .inf. No incluya los archivos DLL dependientes que ya puedan existir en el sistema en este archivo archivador. Por ejemplo, los archivos DLL de MFC se empaquetan en un archivo archivador independiente y el archivo .inf de control hace referencia a ellos.

Para obtener más información sobre cómo crear un archivo CAB, consulte [Creación de un archivo CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>El archivo INF

En el ejemplo siguiente, spindial.inf, se enumeran los archivos auxiliares y la información de versión necesaria para el control Spindial de MFC. Observe que la ubicación de los archivos DLL de MFC es un sitio Web de Microsoft. Microsoft proporciona y firma el archivo mfc42.cab.

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

### <a name="the-object-tag"></a>La \<etiqueta de> OBJECT

En el ejemplo siguiente `<OBJECT>` se muestra el uso de la etiqueta para empaquetar el control de ejemplo Spindial de MFC.

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

En este caso, spindial.cab contendrá dos archivos, spindial.ocx y spindial.inf. El siguiente comando creará el archivo archivador:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

El `-s 6144` parámetro reserva espacio en el archivador para la firma de código.

### <a name="the-version-tag"></a>La etiqueta de versión

Tenga en `#Version` cuenta aquí que la información especificada con un archivo CAB `<OBJECT>` se aplica al control especificado por el parámetro *CLASSID* de la etiqueta.

Dependiendo de la versión especificada, puede forzar la descarga del control. Para obtener especificaciones completas de la `OBJECT` etiqueta, incluido el parámetro *CODEBASE,* consulte la referencia W3C.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Marcar un control seguro para scripting e inicializar

Los controles ActiveX utilizados en las páginas Web deben marcarse como seguros para el scripting y seguros para inicializarlos si de hecho son seguros. Un control seguro no realizará E/S de disco ni accederá directamente a la memoria o registros de una máquina.

Los controles se pueden marcar como seguros para el scripting y seguros para la inicialización a través del registro. Modifique `DllRegisterServer` para agregar entradas similares a las siguientes para marcar el control como seguro para secuencias de comandos y persistencia en el registro. Un método alternativo `IObjectSafety`es implementar .

Definirá GUID (identificadores únicos globales) para el control para marcarlo como seguro para secuencias de comandos y persistencia. Los controles que se pueden crear scripts de forma segura contendrán una entrada del Registro similar a la siguiente:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Los controles que se pueden inicializar de forma segura a partir de datos persistentes se marcan como seguros para la persistencia con una entrada del Registro similar a:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Agregue entradas similares a las siguientes (sustituyendo el identificador de `{06889605-B8D0-101A-91F1-00608CEAD5B3}`clase del control en lugar de ) para asociar las claves con el siguiente identificador de clase:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>Problemas de licencia

Si desea utilizar un control con licencia en una página Web, debe comprobar que el acuerdo de licencia permite su uso en Internet y crear un archivo de paquete de licencia (LPK) para él.

Un control ActiveX con licencia no se cargará correctamente en una página HTML si el equipo que ejecuta Internet Explorer no tiene licencia para usar el control. Por ejemplo, si se creó un control con licencia con Visual C++, la página HTML que usa el control se cargará correctamente en el equipo donde se creó el control, pero no se cargará en un equipo diferente a menos que se incluya información de licencia.

Para utilizar un control ActiveX con licencia en Internet Explorer, debe comprobar el contrato de licencia del proveedor para comprobar que la licencia del control permite:

- Redistribución

- Uso del control en Internet

- Uso del parámetro Codebase

Para usar un control con licencia en una página HTML en un equipo sin licencia, debe generar un archivo de paquete de licencia (LPK). El archivo LPK contiene licencias en tiempo de ejecución para controles con licencia en la página HTML. Este archivo se genera a través de LPK_TOOL. EXE que viene con el SDK de ActiveX.

#### <a name="to-create-an-lpk-file"></a>Para crear un archivo LPK

1. Corre LPK_TOOL. EXE en un equipo con licencia para usar el control.

1. En el cuadro de diálogo Herramienta de creación de **paquetes** de licencias, en el cuadro de lista **Controles disponibles,** seleccione cada control ActiveX con licencia que se usará en la página HTML y haga clic en **Agregar**.

1. Haga clic en **Guardar & Salir** y escriba un nombre para el archivo LPK. Esto creará el archivo LPK y cerrará la aplicación.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Para incrustar un control con licencia en una página HTML

1. Edita tu página HTML. En la página HTML, inserte una \<etiqueta OBJECT> \<para el objeto License Manager antes de cualquier otra etiqueta OBJECT>. El Administrador de licencias es un control ActiveX que se instala con Internet Explorer. Su ID de clase se muestra a continuación. Establezca la propiedad LPKPath del objeto License Manager en la ruta de acceso y el nombre del archivo LPK. Solo puede tener un archivo LPK por página HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Inserte \<la etiqueta OBJECT> para el control con licencia después de la etiqueta License Manager.

   Por ejemplo, a continuación se muestra una página HTML que muestra el control Microsoft Masked Edit. El primer identificador de clase es para el control License Manager, el segundo identificador de clase es para el control Masked Edit. Cambie las etiquetas para que apunten a la ruta de acceso relativa del archivo .lpk que creó anteriormente y agregue una etiqueta de objeto que incluya el identificador de clase del control.

1. Inserte \<el atributo de> EMBED para el archivo LPK, si utiliza el complemento ActiveX de NCompass.

   Si el control se puede ver en otros navegadores habilitados para Active (por ejemplo, Netscape mediante el complemento ActiveX de NCompass), debe agregar la \<sintaxis de> EMBED como se muestra a continuación.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Para obtener más información acerca de las licencias de control, vea [Controles ActiveX: licenciadea un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a>Código de firma

La firma de código está diseñada para identificar el código fuente y para garantizar que el código no ha cambiado desde que se firmó. Dependiendo de la configuración de seguridad del navegador, los usuarios pueden ser advertidos antes de descargar el código. Los usuarios pueden optar por confiar en ciertos propietarios de certificados o empresas, en cuyo caso el código firmado por aquellos de confianza se descargará sin previo aviso. El código está firmado digitalmente para evitar la manipulación.

Asegúrese de que el código final está firmado para que el control se pueda descargar automáticamente sin mostrar mensajes de advertencia de confianza. Para obtener más información sobre cómo firmar código, consulte la documentación de Authenticode en el SDK de ActiveX y consulte [Firma de un archivo CAB](/windows/win32/devnotes/cabinet-api-functions).

Dependiendo de la configuración de confianza y nivel de seguridad del navegador, se puede mostrar un certificado para identificar a la persona o empresa firmante. Si el nivel de seguridad es ninguno, o si el propietario del certificado del control firmado es de confianza, no se mostrará un certificado. Consulte Niveles de seguridad y comportamiento de [control del explorador](#_core_internet_explorer_browser_safety_levels_and_control_behavior) de Internet Explorer para obtener más información sobre cómo la configuración de seguridad del explorador determinará si se descarga el control y se muestra un certificado.

La firma digital garantiza que el código no ha cambiado desde que se firmó. Se toma un hash del código e incrustado en el certificado. Este hash se compara más adelante con un hash del código tomado después de descargar el código, pero antes de que se ejecute. Empresas como Verisign pueden proporcionar claves privadas y públicas necesarias para firmar código. El SDK de ActiveX se incluye con MakeCert, una utilidad para crear certificados de prueba.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>Gestión de la paleta

Los contenedores determinan la paleta y la hacen disponible como una propiedad ambiental, **DISPID_AMBIENT_PALETTE**. Un contenedor (por ejemplo, Internet Explorer) elige una paleta que utilizan todos los controles ActiveX de una página para determinar su propia paleta. Esto evita el parpadeo de la pantalla y presenta un aspecto uniforme.

Un control `OnAmbientPropertyChange` puede anularse para controlar la notificación de cambios en la paleta.

Un control `OnGetColorSet` puede anular para devolver un conjunto de colores para dibujar la paleta. Los contenedores utilizan el valor devuelto para determinar si un control es compatible con la paleta.

Sin las directrices de OCX 96, un control siempre debe realizar su paleta en segundo plano.

Los contenedores más antiguos que no utilizan la propiedad de paleta ambiente enviarán mensajes WM_QUERYNEWPALETTE y WM_PALETTECHANGED. Un control `OnQueryNewPalette` puede `OnPaletteChanged` invalidar y controlar estos mensajes.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Niveles de seguridad y comportamiento de control del navegador Internet Explorer

Un navegador tiene opciones para el nivel de seguridad, configurables por el usuario. Dado que las páginas Web pueden contener contenido activo que podría dañar el equipo de un usuario, los exploradores permiten al usuario seleccionar opciones para el nivel de seguridad. Dependiendo de la forma en que un explorador implementa los niveles de seguridad, es posible que no se descargue un control en absoluto, o mostrará un certificado o un mensaje de advertencia para permitir al usuario elegir en tiempo de ejecución si descargar o no el control. El comportamiento de los controles ActiveX en niveles de seguridad altos, medios y bajos en Internet Explorer se muestra a continuación.

### <a name="high-safety-mode"></a>Modo de alta seguridad

- Los controles sin firmar no se descargarán.

- Los controles firmados mostrarán un certificado si no es de confianza (un usuario puede elegir una opción para confiar siempre en el código de este propietario del certificado a partir de ahora).

- Solo los controles marcados como seguros tendrán datos persistentes y/o serán scriptables.

### <a name="medium-safety-mode"></a>Modo de seguridad media

- Los controles sin firmar mostrarán una advertencia antes de descargar.

- Los controles firmados mostrarán un certificado si no es de confianza.

- Los controles no marcados como seguros mostrarán una advertencia.

### <a name="low-safety-mode"></a>Modo de seguridad baja

- Los controles se descargan sin previo aviso.

- El scripting y la persistencia se producen sin previo aviso.

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Controles ActiveX MFC: Licencias de un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
