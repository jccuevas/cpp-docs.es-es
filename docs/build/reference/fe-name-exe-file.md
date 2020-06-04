---
title: /Fe (Asignar nombre a un archivo ejecutable)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: f0bd8f3a96555cc29d06f74fb44a73bbed32889b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825583"
---
# <a name="fe-name-exe-file"></a>/Fe (Asignar nombre a un archivo ejecutable)

Especifica un nombre y un directorio para el archivo. exe o DLL creado por el compilador.

## <a name="syntax"></a>Sintaxis

> **/Fe**[_rutaDeAcceso_] \
> **/Fe:** _nombreruta_

### <a name="arguments"></a>Argumentos

*Ruta*<br/>
Ruta de acceso relativa o absoluta y nombre de archivo base, o ruta de acceso relativa o absoluta a un directorio, o nombre de archivo base que se va a utilizar para el ejecutable generado.

## <a name="remarks"></a>Observaciones

La opción **/fe** permite especificar el directorio de salida, el nombre del archivo ejecutable de salida, o ambos, para el archivo ejecutable generado. Si *PathName* termina en un separador de ruta de acceso (**&#92;**), se supone que solo especifica el directorio de salida. De lo contrario, se usa el último componente de *PathName* como nombre base del archivo de salida y el resto de *PathName* especifica el directorio de salida. Si *PathName* no tiene ningún separador de ruta de acceso, se supone que especifica el nombre del archivo de salida en el directorio actual. El valor de *PathName* debe ir entre comillas dobles (**"**) si contiene caracteres que no pueden estar en una ruta de acceso corta, como espacios, caracteres extendidos o componentes de ruta de acceso de más de ocho caracteres.

Cuando no se especifica la opción **/fe** , o cuando no se especifica un nombre base de archivo en *PathName*, el compilador asigna al archivo de salida un nombre predeterminado con el nombre base del primer archivo de origen u objeto especificado en la línea de comandos y la extensión. exe o. dll.

Si especifica la opción [/c (compilar sin vincular)](c-compile-without-linking.md) , **/fe** no tiene ningún efecto.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra la página de propiedades**General** del**enlazador** > de **propiedades** > de configuración.

1. Modifique la propiedad **archivo de salida** . Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Ejemplo

La línea de comandos siguiente compila y vincula todos los archivos de código fuente de C en el directorio actual. El archivo ejecutable resultante se denomina PROCESS. exe y se crea en el directorio "C:\Users\nombre Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Ejemplo

La siguiente línea de comandos crea un archivo ejecutable en `C:\BIN` con el mismo nombre base que el primer archivo de código fuente en el directorio actual:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Consulte también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)<br/>
