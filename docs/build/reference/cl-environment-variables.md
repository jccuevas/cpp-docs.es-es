---
title: Variables de entorno de CL
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440248"
---
# <a name="cl-environment-variables"></a>Variables de entorno de CL

La herramienta CL usa las siguientes variables de entorno:

- CL y \_CL_, si se definen. La herramienta CL antepone las opciones y los argumentos definidos en la variable de entorno de CL a los argumentos de la línea de comandos y anexa las opciones y los argumentos definidos en \_CL_, antes del procesamiento.

- INCLUYA, que debe apuntar al subdirectorio \include de la instalación de Visual Studio.

- LIBPATH, que especifica los directorios en los que se van a buscar archivos de metadatos a los que se hace referencia con [#using](../../preprocessor/hash-using-directive-cpp.md). Para obtener más información sobre LIBPATH, vea [#using](../../preprocessor/hash-using-directive-cpp.md).

Puede establecer la variable de entorno de CL o \_CL_ con la siguiente sintaxis:

> SET CL = [[*opción*]... [*archivo*]...] [/Link *Link-opt* ...] \
> ESTABLEZCA \_CL\_= [[*opción*]... [*archivo*]...] [/Link *Link-opt* ...]

Para obtener más información sobre los argumentos de las variables de entorno de CL y \_CL_, consulte [Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md).

Puede usar estas variables de entorno para definir los archivos y las opciones que utiliza con más frecuencia. A continuación, use la línea de comandos para proporcionar más archivos y opciones a CL para fines específicos. Las variables de entorno de CL y \_CL_ se limitan a 1024 caracteres (el límite de entrada de la línea de comandos).

No se puede usar la opción [/d](d-preprocessor-definitions.md) para definir un símbolo que use un signo igual ( **=** ). En su lugar, puede usar el signo de número ( **#** ) para un signo igual. De esta manera, puede utilizar las variables de entorno de CL o \_CL_ para definir constantes de preprocesador con valores explícitos, por ejemplo, `/DDEBUG#1` para definir `DEBUG=1`.

Para obtener información relacionada, vea [establecer variables de entorno](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Ejemplos

El siguiente comando es un ejemplo de la configuración de la variable de entorno de CL:

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Cuando se establece la variable de entorno de CL, si escribe `CL INPUT.C` en la línea de comandos, el comando efectivo pasa a ser:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

En el ejemplo siguiente, un comando de CL sin formato compila los archivos de código fuente FILE1.c y FILE2.c y, a continuación, vincula los archivos objeto FILE1.obj, FILE2.obj y FILE3.obj:

> ESTABLEZCA CL = ARCHIVO1. C ARCHIVO2. Unidad
> ESTABLEZCA \_CL_ = ARCHIVO3. OBJ
> CL

Estas variables de entorno hacen que la llamada a CL tenga el mismo efecto que la siguiente línea de comandos:

> ARCHIVO1 DE CL. C ARCHIVO2. C ARCHIVO3. OBJ

## <a name="see-also"></a>Consulte también

[Establecer opciones del Compilador](compiler-command-line-syntax.md) \
[Opciones del compilador de MSVC](compiler-options.md)
