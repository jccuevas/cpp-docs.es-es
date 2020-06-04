---
title: Error irrecuperable C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203884"
---
# <a name="fatal-error-c1092"></a>Error irrecuperable C1092

La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación

Ha cambiado o agregado un tipo de datos desde la última compilación correcta.

- Editar y continuar no admite cambios en los tipos de datos existentes, incluidas las definiciones de clase, estructura o enumeración. Debe detener la depuración y compilar la aplicación.

- Editar y continuar no admite la adición de nuevos tipos de datos si un archivo de base de datos de programa, como VC*x*0. pdb (donde *x* es la versión C++ principal de visual en uso) es de solo lectura. Para agregar tipos de datos, el compilador debe abrir el archivo. pdb en modo de escritura.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Para quitar este error sin finalizar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

1. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

1. En el menú **Compilar** , elija **Compilar**.

Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).
