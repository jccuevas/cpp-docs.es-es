---
title: Las Variables de entorno de CL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba01a980aa24a3ff695479edd08e88d9ea538dcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cl-environment-variables"></a>Variables de entorno de CL

La herramienta CL usa las siguientes variables de entorno:

- CL y \_CL\_si definido. La herramienta CL antepone las opciones y los argumentos definidos en la variable de entorno de CL a los argumentos de línea de comandos y anexa las opciones y los argumentos definan en \_CL\_, antes del procesamiento.

- INCLUDE, que debe señalar al subdirectorio \include de la instalación de Visual C++.

- LIBPATH, que especifica los directorios donde buscar archivos de metadatos hace referencia con [#using](../../preprocessor/hash-using-directive-cpp.md). Para obtener más información sobre LIBPATH, vea `#using`.

Puede establecer la CL o \_CL\_ variable de entorno mediante la sintaxis siguiente:

> ESTABLECER CL = [[*opción*]... [*archivo*]...] [/ link *vínculo-opt* ...]  
> ESTABLECER \_CL\_= [[*opción*]... [*archivo*]...] [/ link *vínculo-opt* ...]

Para obtener más información sobre los argumentos de la CL y \_CL\_ variables de entorno, consulte [sintaxis de línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).

Puede usar estas variables de entorno para definir los archivos y las opciones que usa con más frecuencia, y puede usar la línea de comandos para definir archivos y opciones específicos para fines específicos. La CL y \_CL\_ variables de entorno están limitadas a 1024 caracteres (el límite de entrada de línea de comandos).

No puede usar la opción /D para definir un símbolo que use un signo igual (=). Puede sustituir el signo de número (#) por un signo igual. De esta manera, puede usar la CL o \_CL\_ variables de entorno para definir constantes de preprocesador con valores explícitos, por ejemplo, `/DDEBUG#1` para definir `DEBUG=1`.

Para obtener información relacionada, consulte [establecer Variables de entorno](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Ejemplos

El siguiente es un ejemplo de configuración de la variable de entorno de CL:

> ESTABLECER CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Cuando se establece esta variable de entorno, si escribe `CL INPUT.C` en la línea de comandos, esto es el comando eficaz:

> CL/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. ENTRADA DE OBJ. C

En el ejemplo siguiente, un comando de CL sin formato compila los archivos de código fuente FILE1.c y FILE2.c y, a continuación, vincula los archivos objeto FILE1.obj, FILE2.obj y FILE3.obj:

> CONJUNTO CL = FILE1. C ARCHIVO2. C  
> ESTABLECER \_CL\_= ARCHIVO3. OBJ  
> CL  

Esto tiene el mismo efecto que la línea de comandos siguiente:

> CL FILE1. C ARCHIVO2. C ARCHIVO3. OBJ

## <a name="see-also"></a>Vea también

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
[Opciones del compilador](../../build/reference/compiler-options.md)
