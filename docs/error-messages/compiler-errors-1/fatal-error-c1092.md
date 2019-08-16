---
title: Error irrecuperable C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: 3268e5b124be40313bdc97b4c95d935ddd4f9160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208551"
---
# <a name="fatal-error-c1092"></a>Error irrecuperable C1092

La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación

Ha cambiado o agregado un tipo de datos desde la última compilación correcta.

- Editar y continuar no admite cambios en los tipos de datos existentes, incluidas las definiciones de clase, estructura o enumeración. Debe detener la depuración y compilar la aplicación.

- Editar y continuar no admite la adición de nuevos tipos de datos si un archivo de base de datos de programa, como vc*x*0.pdb (donde *x* es la versión principal de Visual C++ en uso) es de solo lectura. Para agregar tipos de datos, el compilador debe abrir el archivo .pdb en modo de escritura.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Para quitar este error sin terminar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

1. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

1. En el menú **Compilar** , elija **Compilar**.

Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).