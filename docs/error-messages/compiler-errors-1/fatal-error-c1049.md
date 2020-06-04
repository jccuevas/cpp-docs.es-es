---
title: Error irrecuperable C1049
description: Describe el error irrecuperable del compilador C1049, el argumento numérico no válido y explica cómo resolverlo.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: f2669eec4bafb24f26c405d4fa74a96fe5337d13
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633307"
---
# <a name="fatal-error-c1049"></a>Error irrecuperable C1049

> argumento numérico*value*' no válido

CL. El analizador de la línea de comandos EXE encontró un *valor* en el que esperaba un argumento numérico.

Se puede producir un error C1049 cuando el compilador no puede encontrar un argumento numérico para una de estas opciones del compilador:

[/constexpr: profundidad](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr:](/cpp/build/reference/constexpr-control-constexpr-evaluation)\ de seguimiento
[/constexpr: pasos](/cpp/build/reference/constexpr-control-constexpr-evaluation)

Las opciones del compilador de línea de comandos que esperan un argumento numérico también pueden notificar `Command line error D8004`, `Command line error D8021`, `Command line warning D9002`, `Command line warning D9014`o `Command line warning D9024`.

Para resolver este error, examine la línea de comandos para buscar argumentos no colocados o ausentes. Compruebe que no hay ningún espacio en blanco inesperado entre las opciones y los argumentos. La línea de comandos final se puede generar mediante macros, variables de entorno u otras operaciones del sistema de compilación. Por eso es importante ver la línea de comandos real que se pasa al compilador.

- En archivos de comandos o archivos make, puede usar un comando **echo** para notificar la línea de comandos real.

- En Visual Studio, abra el cuadro de diálogo **páginas de propiedades** del proyecto. En la página **propiedades de configuración** > **CC++ /**  > **General** , cambie la propiedad **suprimir banner de inicio** a **no**. Elija **Aceptar** para guardar los cambios. La ventana de **salida** muestra ahora la línea de comandos al compilar, justo después de la línea de copyright.

Otros sistemas de compilación pueden tener archivos de registro o opciones detalladas para ver los comandos reales usados. Para obtener información, consulte la documentación del sistema de compilación.
