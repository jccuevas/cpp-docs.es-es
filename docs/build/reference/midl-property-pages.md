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
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336254"
---
# <a name="midl-property-pages"></a>Páginas de propiedades MIDL

Las páginas de propiedades MIDL están disponibles como una propiedad de elemento en un archivo . IDL en un proyecto C++ que utiliza COM. Utilícelos para configurar el [compilador MIDL](/windows/win32/midl/using-the-midl-compiler-2). Para obtener información sobre cómo acceder mediante programación a las opciones de MIDL para los proyectos de C++, vea el objeto <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Consulte también Sintaxis general [de la línea de comandos MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Página de propiedades generales

### <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Especifica una o más definiciones, incluidas\[las\]macros MIDL ([/D](/windows/win32/midl/-d)) macros ).

### <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o varios directorios que se agregará\]a la ruta de acceso de inclusión ([/I](/windows/win32/midl/-i)\[path ).

### <a name="additional-metadata-directories"></a>Directorios de metadatos adicionales

Especifique el directorio que contiene el archivo Windows.Foundation.WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[ruta de acceso\]).

### <a name="enable-windows-runtime"></a>Habilitar Windows Runtime

Habilite la semántica de Windows Runtime para crear un archivo de metadatos de Windows ([/winrt](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignorar ruta de inclusión estándar

Ignore los directorios actual e INCLUDE ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>MkTypLib Compatible

Fuerza la compatibilidad con mktyplib.exe versión 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Nivel de advertencia

Selecciona la rigurosidad de los errores de código MIDL ([/W](/windows/win32/midl/-w)).

**Opciones**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

Permite que MIDL trate todas las advertencias como errores ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprimir la visualización del banner de inicio y el mensaje de información ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>C Tipo de Char del compilador

Especifica el tipo de carácter predeterminado del compilador de C que se usará para compilar el código generado. ([/char](/windows/win32/midl/-char) signed-unsigned-ascii7).

**Opciones**

- **Firmado** - Firmado
- **Sin firmar** - Sin firmar
- **Ascii** - Ascii

### <a name="target-environment"></a>Entorno de destino

Especifica el entorno al que se va a dirigir[(/env](/windows/win32/midl/-env) arm32-win32-ia64-x64).

**Opciones**

- **No establecido** - Win32
- **Microsoft Windows de 32 bits** - Win32
- **Microsoft Windows de 64 bits en Itanium** - IA64
- **Microsoft Windows ARM** - ARM
- **Microsoft Windows ARM64** - ARM64
- **Microsoft Windows de 64 bits en x64** - X64

### <a name="generate-stubless-proxies"></a>Generar proxies Stubless

Genere códigos auxiliares totalmente interpretados con extensiones y proxies de intención para interfaces de objetos ([/Oicf](/windows/win32/midl/-oi), [/Oif](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Suprimir advertencias del compilador

Suprimir mensajes de advertencia del compilador ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Modo de configuración de aplicaciones

Permitir atributos ACF seleccionados en el archivo IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>Identificador de configuración regional

Especifica el LCID para los archivos de entrada, los nombres de archivo y las rutas de directorio ([/lcid](/windows/win32/midl/-lcid) DECIMAL).

### <a name="multi-processor-compilation"></a>Compilación multiprocesador

Ejecute varias instancias al mismo tiempo.

## <a name="output-property-page"></a>Página de propiedades de salida

### <a name="output-directory"></a>Directorio de salida

Especifica el directorio de salida ([/out](/windows/win32/midl/-out) [directorio]).

### <a name="metadata-file"></a>Archivo de metadatos

Especifica el nombre del archivo de metadatos generado (nombre de archivo[/winmd).](/windows/win32/midl/-winmd)

### <a name="header-file"></a>Archivo de encabezado

Especifica el nombre del archivo de encabezado generado (nombre de archivo[/h).](/windows/win32/midl/-h)

### <a name="dlldata-file"></a>Archivo DllData

Especifica el nombre del archivo DLLDATA ( nombre de archivo[/dlldata).](/windows/win32/midl/-dlldata)

### <a name="iid-file"></a>Archivo IID

Especifica el nombre del archivo de identificador de interfaz ( nombre de archivo[/iid).](/windows/win32/midl/-iid)

### <a name="proxy-file"></a>Archivo proxy

Especifica el nombre del archivo proxy ([/proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Generar biblioteca de tipos

Especifique no generar una biblioteca de tipos ([/notlb] para no).

### <a name="type-library"></a>Biblioteca de tipos

Especifica el nombre del archivo de biblioteca de tipos ([/tlb](/windows/win32/midl/-tlb) filename).

### <a name="generate-client-stub-files"></a>Generar archivos Stub de cliente

Generar solo el archivo de código auxiliar de cliente ([/client](/windows/win32/midl/-client) [stub-none]).

**Opciones**

- **Stub** - Stub
- **Ninguno** - Ninguno

### <a name="generate-server-stub-files"></a>Generar archivos Stub del servidor

Generar solo el archivo de código auxiliar del servidor ([/server](/windows/win32/midl/-server) [stub-none]).

**Opciones**

- **Stub** - Stub
- **Ninguno** - Ninguno

### <a name="client-stub-file"></a>Archivo Stub del cliente

Especifique el archivo de código auxiliar del cliente ([/cstub](/windows/win32/midl/-cstub) [file]).

### <a name="server-stub-file"></a>Archivo Stub del servidor

Especifique el archivo de código auxiliar del servidor ([/sstub](/windows/win32/midl/-sstub) [archivo]).

### <a name="type-library-format"></a>Formato de biblioteca de tipos

Especifica el formato de archivo de biblioteca de tipos ([/oldtlb/newtlb]).

**Opciones**

- **NewFormat** - Nuevo formato
- **OldFormat** - Formato antiguo

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

### <a name="c-preprocess-options"></a>C Opciones de preproceso

Especifica los modificadores que se pasan al preprocesador del compilador de C ([modificadores /cpp_opt).](/windows/win32/midl/-cpp-opt)

### <a name="undefine-preprocessor-definitions"></a>Anular definiciones del preprocesador

Especifica una o más definiciones, incluidas las macros MIDL ([/U](/windows/win32/midl/-U) [macros]).

### <a name="enable-error-checking"></a>Activar comprobación de errores

Seleccione la opción de comprobación de errores ([/error all-none]).

**Opciones**

- **EnableCustom** - Todos
- **Todos** - Todos - Todos
- **Ninguno** - Ninguno

### <a name="check-allocations"></a>Comprobar asignaciones

Compruebe si hay errores de memoria insuficiente (asignación de[/error).](/windows/win32/midl/-error)

### <a name="check-bounds"></a>Comprobar límites

Compruebe el tamaño frente a la especificación de longitud de transmisión ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Comprobar rango de enum

Compruebe que los valores de enumeración estén en el rango permitido ([/error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Compruebe los punteros de referencia

Compruebe que los punteros ref no sean nulos ([/error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Comprobar datos de Stub

Emita una comprobación adicional para la validez de los datos del lado del servidor ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Anteponer se a la habitación 'ABI'

Anteponga el espacio de nombres 'ABI' a todos los tipos.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Validar parámetros

Genere información adicional para validar parámetros ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Alineación de miembros de Struct

Especifica el nivel de embalaje de las estructuras en el sistema de destino (/ZpN).

**Opciones**

- **No establecido** - No establecido
- **1 Byte** - Zp1
- **2 Byte** - Zp2
- **4 Byte** - Zp4
- **8 Bytes** - Zp8

### <a name="redirect-output"></a>Redirección de salida

Redirige la salida de la pantalla a un archivo ([archivo /o).](/windows/win32/midl/-o)

### <a name="minimum-target-system"></a>Sistema de objetivo mínimo

Establezca el sistema de destino mínimo ([/target](/windows/win32/midl/-target) STRING).
