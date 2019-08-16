---
title: Advertencia de las herramientas del vinculador LNK4098
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408100"
---
# <a name="linker-tools-warning-lnk4098"></a>Advertencia de las herramientas del vinculador LNK4098

> DEFAULTLIB '*biblioteca*' entra en conflicto con otras bibliotecas; use/NODEFAULTLIB:*biblioteca*

Está intentando vincular con bibliotecas incompatibles.

> [!NOTE]
> Ahora, las bibliotecas en tiempo de ejecución contienen directivas para evitar mezclar distintos tipos. Recibirá esta advertencia si se intenta usar diferentes tipos o de depuración y las versiones que no sean de depuración de la biblioteca en tiempo de ejecución en el mismo programa. Por ejemplo, si compila un archivo para usar un tipo de biblioteca en tiempo de ejecución y otro para usar otro tipo (por ejemplo, debug frente a la venta directa) y se intenta vincularlos, aparecerá esta advertencia. Se deben compilar todos los archivos de código fuente para usar la misma biblioteca de tiempo de ejecución. Para obtener más información, consulte el [/MD, / MT, /LD (utilizar la biblioteca de tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md) opciones del compilador.

Puede usar el enlazador [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) conmutador para averiguar qué bibliotecas busca el vinculador. Por ejemplo, cuando el archivo ejecutable usa las bibliotecas en tiempo de ejecución multiproceso, que no sean de depuración, debe incluir la lista notifican LIBCMT.lib y no LIBCMTD.lib, MSVCRT.lib o MSVCRTD.lib. Puede indicar al enlazador que omita las bibliotecas en tiempo de ejecución incorrectas mediante el uso de [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para cada biblioteca que desea omitir.

La siguiente tabla muestra qué bibliotecas deben omitirse según la biblioteca de tiempo de ejecución que desee usar. En la línea de comandos, use uno **/NODEFAULTLIB** opción para cada biblioteca pasar por alto. En el IDE de Visual Studio, separar las bibliotecas para pasar por alto por puntos y coma en el **Omitir bibliotecas predeterminadas específicas** propiedad.

| Para usar esta biblioteca en tiempo de ejecución | Omitir estas bibliotecas |
|-----------------------------------|----------------------------|
| Multiproceso (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| Multiproceso con DLL (msvcrt.lib) | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| Depuración multiproceso (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| Depuración multiproceso con DLL (msvcrtd.lib) | libcmt.lib; msvcrt.lib; libcmtd.lib |

Por ejemplo, si ha recibido esta advertencia y desea crear un archivo ejecutable usa la versión DLL de no depuración, de las bibliotecas en tiempo de ejecución, puede utilizar las siguientes opciones con el vinculador:

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```