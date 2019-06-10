---
title: Variables de entorno de CL
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821536"
---
# <a name="cl-environment-variables"></a>Variables de entorno de CL

La herramienta CL usa las siguientes variables de entorno:

- CL y \_CL_, si ha definido. La herramienta CL antepone las opciones y argumentos definidos en la variable de entorno de CL a los argumentos de línea de comandos y anexa las opciones y argumentos definan en \_CL_ antes del procesamiento.

- ENTRE los que debe apuntar al subdirectorio \include de la instalación de Visual Studio.

- LIBPATH, que especifica los directorios donde buscar archivos de metadatos al que hace referencia con [#using](../../preprocessor/hash-using-directive-cpp.md). Para obtener más información sobre LIBPATH, vea [#using](../../preprocessor/hash-using-directive-cpp.md).

Puede establecer la CL o \_variable de entorno CL_ utilizando la sintaxis siguiente:

> ESTABLECER CL = [[*opción*]... [*archivo*]...] [/ link *vínculo-opt* ...] \
> SET \_CL\_=[ [*option*] ... [*file*] ...] [/link *link-opt* ...]

Para obtener más información sobre los argumentos de la CL y \_CL_ variables de entorno, vea [sintaxis de línea de comandos del compilador de MSVC](compiler-command-line-syntax.md).

Puede usar estas variables de entorno para definir los archivos y las opciones que se usan con más frecuencia. A continuación, usar la línea de comandos para proporcionar a más de los archivos y opciones de CL para fines específicos. La CL y \_variables de entorno CL_ están limitadas a 1024 caracteres (el límite de entrada de línea de comandos).

No puede usar el [/D](d-preprocessor-definitions.md) opción para definir un símbolo que se usa un signo igual ( **=** ). En su lugar, puede usar el signo de número ( **#** ) por un signo igual. De este modo, puede usar el CL o \_variables de entorno CL_ para definir constantes de preprocesador con valores explícitos, por ejemplo, `/DDEBUG#1` para definir `DEBUG=1`.

Para obtener información relacionada, consulte [establecer Variables de entorno](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Ejemplos

El comando siguiente es un ejemplo de configuración de la variable de entorno de CL:

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Cuando se establece la variable de entorno de CL, si escribe `CL INPUT.C` en la línea de comandos, se convierte en el comando eficaz:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

En el ejemplo siguiente, un comando de CL sin formato compila los archivos de código fuente FILE1.c y FILE2.c y, a continuación, vincula los archivos objeto FILE1.obj, FILE2.obj y FILE3.obj:

> CONJUNTO DE CL = FILE1. C FILE2. C \
> ESTABLECER \_CL_ = FILE3. OBJ \
> CL

Estas variables de entorno realiza la llamada a CL tiene el mismo efecto que la línea de comandos siguiente:

> CL FILE1.C FILE2.C FILE3.OBJ

## <a name="see-also"></a>Vea también

[Establecer opciones del compilador](compiler-command-line-syntax.md) \
[Opciones del compilador de MSVC](compiler-options.md)
