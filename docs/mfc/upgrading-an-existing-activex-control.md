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
ms.openlocfilehash: 06c39240d3718f6fbaa15b46abeb8ac9132b5945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510866"
---
# <a name="upgrading-an-existing-activex-control"></a>Actualizar un control ActiveX existente

Los controles ActiveX existentes (antes controles OLE) se pueden usar en Internet sin modificarlos. Sin embargo, puede que desee modificar los controles para mejorar su rendimiento.

> [!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Al utilizar el control en una página web, existen consideraciones adicionales. El archivo. ocx y todos los archivos auxiliares deben estar en el equipo de destino o descargarse a través de Internet. Esto hace que el tamaño del código y el tiempo de descarga sea una consideración importante. Las descargas se pueden empaquetar en un archivo. CAB firmado. Puede marcar el control como seguro para el scripting y como seguro para la inicialización.

En este artículo se tratan los siguientes temas:

- [Empaquetado del código para la descarga](#_core_packaging_code_for_downloading)

- [Marcar un control seguro para scripting e inicialización](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problemas de licencias](#_core_licensing_issues)

- [Firmar código](#_core_signing_code)

- [Administrar la paleta](#_core_managing_the_palette)

- [Niveles de seguridad del explorador de Internet Explorer y comportamiento del control](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

También puede Agregar optimizaciones, como se describe en [controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md). Los monikers se pueden usar para descargar propiedades y blobs grandes de forma asincrónica, tal como se describe en [controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a>Empaquetado del código para la descarga

Para obtener más información sobre este tema, vea [empaquetar controles ActiveX](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>La etiqueta codebase

Los controles ActiveX se incrustan en páginas web `<OBJECT>` mediante la etiqueta. El `CODEBASE` parámetro de la `<OBJECT>` etiqueta especifica la ubicación desde la que se va a descargar el control. `CODEBASE`puede apuntar a varios tipos de archivo diferentes correctamente.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Usar la etiqueta codebase con un archivo OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Esta solución solo descarga el archivo. ocx del control y requiere que los archivos dll auxiliares estén instalados en el equipo cliente. Esto funcionará con los controles ActiveX de Internet Explorer y MFC compilados con Visual C++, ya que Internet Explorer se suministra C++ con los archivos dll auxiliares para los controles visuales. Si se usa otro explorador de Internet que admita controles ActiveX para ver este control, esta solución no funcionará.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Usar la etiqueta codebase con un archivo INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Un archivo. inf controlará la instalación de un archivo. ocx y sus archivos auxiliares. No se recomienda este método porque no es posible firmar un archivo. inf (vea [firmar código](#_core_signing_code) para punteros en la firma de código).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Usar la etiqueta codebase con un archivo. CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Los archivos. cab son el método recomendado para empaquetar controles ActiveX que usan MFC. El empaquetado de un control ActiveX MFC en un archivo. inf permite incluir un archivo. inf para controlar la instalación del control ActiveX y los archivos DLL dependientes (como los archivos dll de MFC). El uso de un archivo. CAB comprime automáticamente el código para una descarga más rápida. Si usa un archivo. cab para la descarga de componentes, es más rápido firmar todo el archivo. cab que cada componente individual.

### <a name="creating-cab-files"></a>Crear archivos. CAB

Las herramientas para crear archivos. cab ahora forman parte del [SDK de Windows 10](https://dev.windows.com/downloads/windows-10-sdk).

El archivo. cab al que `CODEBASE` apunta debe contener el archivo. ocx del control ActiveX y un archivo. inf para controlar su instalación. El archivo. cab se crea especificando el nombre del archivo de control y un archivo. inf. No incluya archivos DLL dependientes que ya existan en el sistema de este archivo. cab. Por ejemplo, los archivos dll de MFC se empaquetan en un archivo. cab independiente al que se hace referencia mediante el archivo. inf de control.

Para obtener más información sobre cómo crear un archivo. CAB, consulte [crear un archivo. cab](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>El archivo INF

En el ejemplo siguiente, spindial. inf, se enumeran los archivos auxiliares y la información de versión necesaria para el control spindial de MFC. Observe que la ubicación de los archivos dll de MFC es un sitio web de Microsoft. Microsoft proporciona y firma Mfc42. cab.

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

### <a name="the-object-tag"></a>Etiqueta \<de > de objeto

En el ejemplo siguiente se muestra el `<OBJECT>` uso de la etiqueta para empaquetar el control de ejemplo spindial de MFC.

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

En este caso, spindial. cab contendrá dos archivos: spindial. ocx y spindial. inf. El siguiente comando generará el archivo. cab:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

El `-s 6144` parámetro Reserva espacio en el archivo. cab para la firma de código.

### <a name="the-version-tag"></a>La etiqueta de versión

Tenga en cuenta que `#Version` la información especificada con un archivo. cab se aplica al control especificado por el parámetro *CLASSID* de la `<OBJECT>` etiqueta.

En función de la versión especificada, puede forzar la descarga del control. Para obtener especificaciones completas de `OBJECT` la etiqueta que incluye el parámetro codebase, vea la referencia del W3C.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Marcar un control seguro para scripting e inicialización

Los controles ActiveX usados en páginas web se deben marcar como seguros para scripting y como seguros para la inicialización si son seguros. Un control seguro no realizará la e/s de disco ni tendrá acceso a la memoria o a los registros de un equipo directamente.

Los controles se pueden marcar como seguros para scripting y seguros para la inicialización a través del registro. Modifique `DllRegisterServer` para agregar entradas similares a las siguientes para marcar el control como seguro para el scripting y la persistencia en el registro. Un método alternativo es implementar `IObjectSafety`.

Definirá los GUID (identificadores únicos globales) del control para que se marquen como seguros para el scripting y para la persistencia. Los controles que se pueden incluir en un script de forma segura contendrán una entrada del registro similar a la siguiente:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Los controles que se pueden inicializar de forma segura a partir de datos persistentes se marcan como seguros para la persistencia con una entrada del registro similar a:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Agregue entradas similares a las siguientes (sustituyendo el identificador de clase del control en lugar `{06889605-B8D0-101A-91F1-00608CEAD5B3}`de) para asociar las claves con el siguiente identificador de clase:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a>Problemas de licencias

Si desea utilizar un control con licencia en una página web, debe comprobar que el contrato de licencia permite su uso en Internet y crear un archivo de paquete de licencia (LPK) para él.

Un control ActiveX con licencia no se cargará correctamente en una página HTML si el equipo que ejecuta Internet Explorer no tiene licencia para usar el control. Por ejemplo, si se compiló un control con licencia mediante C++visual, la página HTML que usa el control se cargará correctamente en el equipo donde se compiló el control, pero no se cargará en un equipo diferente a menos que se incluya la información de licencia.

Para usar un control ActiveX con licencia en Internet Explorer, debe consultar el contrato de licencia del proveedor para comprobar que la licencia del control permite lo siguiente:

- Redistribución

- Uso del control en Internet

- Uso del parámetro CODEBASE

Para usar un control con licencia en una página HTML en un equipo sin licencia, debe generar un archivo de paquete de licencia (LPK). El archivo LPK contiene licencias en tiempo de ejecución para los controles con licencia en la página HTML. Este archivo se genera a través de LPK_TOOL. EXE que se incluye con el SDK de ActiveX.

#### <a name="to-create-an-lpk-file"></a>Para crear un archivo LPK

1. Ejecute LPK_TOOL. EXE en un equipo con licencia para usar el control.

1. En el cuadro de diálogo **herramienta de creación de paquetes de licencias** , en el cuadro de lista **controles disponibles** , seleccione cada control ActiveX con licencia que se utilizará en la página HTML y haga clic en **Agregar**.

1. Haga clic en **guardar & salir** y escriba un nombre para el archivo lpk. Se creará el archivo LPK y se cerrará la aplicación.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Para incrustar un control con licencia en una página HTML

1. Edite la página HTML. En la página HTML, inserte un \<objeto > etiqueta para el objeto de administrador de licencias antes \<de cualquier otro objeto > etiquetas. El administrador de licencias es un control ActiveX que se instala con Internet Explorer. A continuación se muestra su identificador de clase. Establezca la propiedad LPKPath del objeto de administrador de licencias en la ruta de acceso y el nombre del archivo LPK. Solo puede tener un archivo LPK por cada página HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Inserte el \<objeto > etiqueta para el control con licencia después de la etiqueta del administrador de licencias.

   Por ejemplo, a continuación se muestra una página HTML que muestra el control de edición con máscara de Microsoft. El primer identificador de clase es para el control de administrador de licencias, el segundo identificador de clase es para el control de edición con máscara. Cambie las etiquetas para que apunten a la ruta de acceso relativa del archivo. lpk que creó anteriormente y agregue una etiqueta de objeto que incluya el identificador de clase del control.

1. Inserte el \<atributo embed > del archivo LPK, si usa el complemento ActiveX NCompass.

   Si el control se puede ver en otros exploradores habilitados activos (por ejemplo, Netscape con el complemento ActiveX NCompass), debe agregar la \<sintaxis de embed > como se muestra a continuación.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Para obtener más información sobre las licencias de control [, vea controles ActiveX: Conceder licencias a un](../mfc/mfc-activex-controls-licensing-an-activex-control.md)control ActiveX.

##  <a name="_core_signing_code"></a>Firmar código

La firma de código está diseñada para identificar el origen de código y para garantizar que el código no ha cambiado desde que se firmó. En función de la configuración de seguridad del explorador, es posible que se advierta a los usuarios antes de descargar el código. Los usuarios pueden optar por confiar en determinados propietarios o compañías de certificados, en cuyo caso el código firmado por esos de confianza se descargará sin previo aviso. El código está firmado digitalmente para evitar alteraciones.

Asegúrese de que el código final está firmado para que el control pueda descargarse automáticamente sin mostrar mensajes de advertencia de confianza. Para obtener más información sobre cómo firmar código, consulte la documentación de Authenticode en el SDK de ActiveX y vea [firmar un archivo. cab](/windows/win32/devnotes/cabinet-api-functions).

En función de la configuración del nivel de seguridad de confianza y del explorador, es posible que se muestre un certificado para identificar la persona o compañía de firma. Si el nivel de seguridad es None, o si el propietario del certificado del control firmado es de confianza, no se mostrará ningún certificado. Consulte [niveles de seguridad del explorador de Internet Explorer y comportamiento del control](#_core_internet_explorer_browser_safety_levels_and_control_behavior) para obtener detalles sobre cómo la configuración de seguridad del explorador determinará si el control se descarga y se muestra un certificado.

La firma digital garantiza que el código no ha cambiado desde que se firmó. Se toma un hash del código y se inserta en el certificado. Este hash se compara posteriormente con un hash del código tomado después de descargar el código, pero antes de que se ejecute. Las compañías como VeriSign pueden proporcionar claves públicas y privadas necesarias para firmar código. El SDK de ActiveX se incluye en MakeCert, una utilidad para crear certificados de prueba.

##  <a name="_core_managing_the_palette"></a>Administrar la paleta

Los contenedores determinan la paleta y hacen que esté disponible como una propiedad de ambiente, **DISPID_AMBIENT_PALETTE**. Un contenedor (por ejemplo, Internet Explorer) elige una paleta que se usa en todos los controles ActiveX de una página para determinar su propia paleta. Esto evita el parpadeo de la pantalla y presenta un aspecto coherente.

Un control puede invalidar `OnAmbientPropertyChange` para controlar la notificación de cambios en la paleta.

Un control puede invalidar `OnGetColorSet` para devolver un conjunto de colores para dibujar la paleta. Los contenedores usan el valor devuelto para determinar si un control tiene en cuenta la paleta.

En las instrucciones de OCX 96, un control siempre debe obtener su paleta en segundo plano.

Los contenedores más antiguos que no usan la propiedad de paleta ambiente enviarán mensajes WM_QUERYNEWPALETTE y WM_PALETTECHANGED. Un control puede `OnQueryNewPalette` invalidar `OnPaletteChanged` y controlar estos mensajes.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Niveles de seguridad del explorador de Internet Explorer y comportamiento del control

Un explorador tiene opciones para el nivel de seguridad, que puede configurar el usuario. Dado que las páginas web pueden contener contenido activo que podría dañar el equipo de un usuario, los exploradores permiten al usuario seleccionar opciones de nivel de seguridad. En función de la forma en que un explorador implementa los niveles de seguridad, es posible que un control no se descargue en absoluto, o mostrará un certificado o un mensaje de advertencia para permitir al usuario elegir en tiempo de ejecución si descargar o no el control. A continuación se muestra el comportamiento de los controles ActiveX en niveles de seguridad alta, media y baja en Internet Explorer.

### <a name="high-safety-mode"></a>Modo de seguridad alta

- No se descargarán los controles sin firmar.

- Los controles firmados mostrarán un certificado si no es de confianza (un usuario puede elegir una opción para confiar siempre en el código de este propietario del certificado de ahora en).

- Solo los controles marcados como seguros tendrán datos persistentes o convertibles en scripts.

### <a name="medium-safety-mode"></a>Modo de seguridad media

- Los controles sin firmar mostrarán una advertencia antes de la descarga.

- Los controles firmados mostrarán un certificado si no es de confianza.

- Los controles no marcados como seguros mostrarán una advertencia.

### <a name="low-safety-mode"></a>Modo de seguridad baja

- Los controles se descargan sin previo aviso.

- El scripting y la persistencia se producen sin previo aviso.

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Controles ActiveX de MFC: otorgar licencias a un control ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
