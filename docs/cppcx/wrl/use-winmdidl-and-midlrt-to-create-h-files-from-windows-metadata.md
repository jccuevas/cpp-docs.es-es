---
title: 'Cómo: Usar winmdidl.exe y midlrt.exe para crear archivos .h desde metadatos de Windows'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: bceb4aff22f6ebba9c8705b3b5a55d0478f244c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213543"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Cómo: Usar winmdidl.exe y midlrt.exe para crear archivos .h desde metadatos de Windows

Winmdidl.exe y midlrt.exe permiten la interacción de nivel COM entre el código de C++ nativo y los componentes de Windows Runtime. Winmdidl.exe toma como entrada un archivo .winmd que contiene los metadatos para un componente de Windows Runtime y genera un archivo IDL. Midlrt.exe convierte ese archivo IDL en archivos de encabezado que el código de C++ puede utilizar. Ambas herramientas se ejecutan en la línea de comandos.

Estas herramientas se utilizan en dos escenarios principales:

- Crear un archivo IDL personalizado y archivos de encabezado de modo que una aplicación de C++ escrita mediante la Biblioteca de plantillas de Windows Runtime (WRL) pueda utilizar un componente personalizado de Windows Runtime.

- Generar archivos de proxy y código auxiliar para los tipos de eventos definidos por el usuario en un componente de Windows Runtime. Para obtener más información, vea [eventos personalizados y descriptores de acceso de eventos en Windows Runtime componentes](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Estas herramientas solo son necesarias para analizar archivos .winmd personalizados. Los archivos .idl y .h para componentes del sistema operativo Windows se generan automáticamente. De forma predeterminada, en Windows 8.1, se encuentran en la carpeta \Archivos de programa (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Ubicación de las herramientas

De forma predeterminada en [Windows 8.1, winmdidl. exe y midlrt. exe se encuentran en C:\Archivos de programa (x86) \Windows Kits\8.1\\. Hay otras versiones de las herramientas disponibles en las carpetas \bin\x86\ y \bin\x64\.

## <a name="winmdidl-command-line-arguments"></a>Argumentos de la línea de comandos de Winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Impide que se muestre en la consola el mensaje de copyright y el número de versión de winmdidl.

**/suppressversioncheck**<br/>
No se usa.

**/Time**<br/>
Muestra el tiempo de ejecución total en el resultado de la consola.

**/outdir:** <em>dir</em><br/>
Especifica un directorio de salida. Si la ruta de acceso contiene espacios en blanco, utilice comillas. El directorio de salida predeterminado es *\<unidad >* : \usuarios\\ *\<username >* \AppData\Local\VirtualStore\Program files (x86) \microsoft Visual Studio 12,0\\.

**/banner:** <em>archivo</em><br/>
Especifica un archivo que contiene el texto personalizado que se va a anteponer al mensaje de copyright predeterminado y al número de versión de winmdidl en la parte superior del archivo .idl generado. Si la ruta de acceso contiene espacios en blanco, utilice comillas.

**/utf8**<br/>
Hace que el archivo tenga formato UTF-8.

*Winmdfile*<br/>
Nombre del archivo .winmd que se va a analizar. Si la ruta de acceso contiene espacios en blanco, utilice comillas.

## <a name="midlrt-command-line-arguments"></a>Argumentos de la línea de comandos de Midlrt

Vea [MIDLRT y Windows Runtime componentes](/windows/win32/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Ejemplos

En el ejemplo siguiente se muestra un comando winmdidl en un símbolo del sistema de Visual Studio x86. Especifica un directorio de salida y un archivo que contiene el texto de la pancarta especial que se va a agregar al archivo .idl generado.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

En el ejemplo siguiente se muestra la pantalla de la consola de winmdidl que indica que la operación se realizó correctamente.

**Generar c:\users\giraffe\documents\\\ Test_for_winmdidl. idl**

A continuación, se ejecuta midlrt en el archivo IDL generado. Observe que el argumento **metadata_dir** se especifica después del nombre del archivo. idl. La ruta de acceso de \WinMetadata\ es obligatoria; es la ubicación de windows.winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\username\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Observaciones

El archivo de salida de una operación de winmdidl tiene el mismo nombre que el archivo de entrada, pero tiene la extensión de nombre de archivo .idl.

Si va a desarrollar un componente de Windows en tiempo de ejecución al que se obtendrá acceso desde WRL, puede especificar que winmdidl.exe y midlrt.exe se ejecuten como pasos posteriores a la compilación para que se generen los archivos .idl y .h en cada compilación. Para obtener un ejemplo, vea [generar eventos en componentes de Windows Runtime](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).
