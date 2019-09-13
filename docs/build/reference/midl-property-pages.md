---
title: Páginas de propiedades del compilador MIDL
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: e9c9cb75d326642c86405992a4bf9d7da9e578df
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927689"
---
# <a name="midl-property-pages"></a>Páginas de propiedades MIDL

Las páginas de propiedades MIDL están disponibles como una propiedad Item en. Archivo IDL en un C++ proyecto que usa com. Úselos para configurar el [compilador de MIDL](/windows/win32/midl/using-the-midl-compiler-2). Para obtener información sobre cómo acceder mediante programación a las opciones de MIDL para los proyectos de C++, vea el objeto <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Vea también [Sintaxis general de la línea de comandos de MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Página de propiedades general

### <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Especifica una o más definiciones, incluidas las macros MIDL ([/D](/windows/win32/midl/-d))\[macros\]).

### <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o más directorios que se van a agregar a la ruta de\]acceso de inclusión ([/i](/windows/win32/midl/-i)\[path).

### <a name="additional-metadata-directories"></a>Directorios de metadatos adicionales

Especifique el directorio que contiene el archivo Windows.Foundation.WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[path\]).

### <a name="enable-windows-runtime"></a>Habilitar Windows Runtime

Habilite la semántica de Windows Runtime para crear el archivo de metadatos de Windows ([/winrt](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Omitir ruta de acceso de inclusión estándar

Omitir los directorios actuales y de inclusión ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Compatible con MkTypLib

Fuerza la compatibilidad con MkTypLib. exe versión 2,03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Nivel de advertencia

Selecciona la rigurosidad de los errores de código MIDL ([/w](/windows/win32/midl/-w)).

**Posibilidad**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

Permite que MIDL trate todas las advertencias como errores ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprimir la presentación de la pancarta de inicio y el mensaje de información ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>Tipo char del compilador de C

Especifica el tipo de carácter predeterminado del compilador de C que se utilizará para compilar el código generado. ([/Char](/windows/win32/midl/-char) firmado | unsigned | ascii7).

**Posibilidad**

- **Firmada**
- **Unsigned** : sin signo
- **ASCII-ASCII**

### <a name="target-environment"></a>Entorno de destino

Especifica el entorno de destino ([/env](/windows/win32/midl/-env) ARM32 | Win32 | ia64 | x64).

**Posibilidad**

- **No establecido** : Win32
- **Microsoft Windows 32-bit** -Win32
- **Microsoft Windows 64 bits en Itanium** -ia64
- **Microsoft Windows ARM** -ARM
- **ARM64 Microsoft Windows** -ARM64
- **Microsoft Windows 64 bits en x64** -x64

### <a name="generate-stubless-proxies"></a>Generación de proxies instubs

Genere código auxiliar completamente interpretado con extensiones y servidores proxy sin código auxiliar para las interfaces de objeto ([/Oicf](/windows/win32/midl/-oi), [/OIF](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Suprimir advertencias del compilador

Suprimir mensajes de advertencia del compilador ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Modo de configuración de la aplicación

Permite los atributos ACF seleccionados en el archivo IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>IDENTIFICADOR de configuración regional

Especifica el LCID para los archivos de entrada, los nombres de archivo y las rutas de acceso de directorio ([/LCID](/windows/win32/midl/-lcid) decimal).

### <a name="multi-processor-compilation"></a>Compilación de varios procesadores

Ejecutar varias instancias al mismo tiempo.

## <a name="output-property-page"></a>Página de propiedades de salida

### <a name="output-directory"></a>Directorio de salida

Especifica el directorio de salida ([/out](/windows/win32/midl/-out) [directorio]).

### <a name="metadata-file"></a>Archivo de metadatos

Especifica el nombre del archivo de metadatos generado ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Archivo de encabezado

Especifica el nombre del archivo de encabezado generado ([/h](/windows/win32/midl/-h) nombredearchivo).

### <a name="dlldata-file"></a>Archivo DllData

Especifica el nombre del archivo DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>Archivo IID

Especifica el nombre del archivo de identificador de interfaz ([/IID](/windows/win32/midl/-iid) filename).

### <a name="proxy-file"></a>Archivo proxy

Especifica el nombre del archivo de proxy ([/proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Generar biblioteca de tipos

Especifique que no se genere una biblioteca de tipos ([/notlb] para no).

### <a name="type-library"></a>Biblioteca de tipos

Especifica el nombre del archivo de biblioteca de tipos ([/tlb](/windows/win32/midl/-tlb) nombredearchivo).

### <a name="generate-client-stub-files"></a>Generar archivos de código auxiliar de cliente

Generar solo el archivo de código auxiliar de cliente ([/Client](/windows/win32/midl/-client) [stub | None]).

**Posibilidad**

- Código **auxiliar stub**
- **Ninguno** : ninguno

### <a name="generate-server-stub-files"></a>Generar archivos de código auxiliar de servidor

Generar solo el archivo de código auxiliar de servidor ([/Server](/windows/win32/midl/-server) [stub | None]).

**Posibilidad**

- Código **auxiliar stub**
- **Ninguno** : ninguno

### <a name="client-stub-file"></a>Archivo de código auxiliar de cliente

Especifique el archivo de código auxiliar de cliente ([/cstub](/windows/win32/midl/-cstub) [archivo]).

### <a name="server-stub-file"></a>Archivo de código auxiliar de servidor

Especifique el archivo de código auxiliar del servidor ([/sstub](/windows/win32/midl/-sstub) [archivo]).

### <a name="type-library-format"></a>Formato de la biblioteca de tipos

Especifica el formato de archivo de la biblioteca de tipos ([/oldtlb |/newtlb]).

**Posibilidad**

- **NewFormat** -nuevo formato
- **OldFormat** : formato antiguo

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

### <a name="c-preprocess-options"></a>Opciones de preprocesamiento de C

Especifica los modificadores que se van a pasar al preprocesador del compilador de C (modificadores[/cpp_opt](/windows/win32/midl/-cpp-opt) ).

### <a name="undefine-preprocessor-definitions"></a>Anular definiciones del preprocesador

Especifica una o más anulaciones de definición, incluidas las macros MIDL ([/u](/windows/win32/midl/-U) [macros]).

### <a name="enable-error-checking"></a>Habilitar comprobación de errores

Seleccione la opción de comprobación de errores ([/error All | None]).

**Posibilidad**

- **EnableCustom** -All
- **Todo todo**
- **Ninguno** : ninguno

### <a name="check-allocations"></a>Comprobar asignaciones

Compruebe si hay errores de memoria insuficiente ([/error](/windows/win32/midl/-error) Allocation).

### <a name="check-bounds"></a>Comprobar límites

Compruebe el tamaño y la especificación de longitud de la transmisión ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Comprobar intervalo de enumeración

Compruebe que los valores de enumeración estén en el intervalo permitido ([/error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Comprobar punteros de referencia

Compruebe que los punteros de referencia no sean null ([/error](/windows/win32/midl/-error) Ref).

### <a name="check-stub-data"></a>Comprobar datos de código auxiliar

Emita una comprobación adicional para la validez de los datos de código auxiliar del lado del servidor ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Anteponer al espacio de nombres ' ABI '

Anteponga el espacio de nombres ' ABI ' a todos los tipos.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Validar parámetros

Generar información adicional para validar los parámetros ([/Robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Alineación de miembros de struct

Especifica el nivel de empaquetado de las estructuras en el sistema de destino (/ZpN).

**Posibilidad**

- **No establecido** : no establecido
- **1 byte** : Zp1
- **2 bytes** : Zp2
- **4 bytes** -Zp4
- **8 bytes** Zp8

### <a name="redirect-output"></a>Redirigir la salida

Redirige la salida de la pantalla a un archivo ([/o](/windows/win32/midl/-o) File).

### <a name="minimum-target-system"></a>Sistema de destino mínimo

Establezca el sistema de destino mínimo (cadena[/target](/windows/win32/midl/-target) ).



