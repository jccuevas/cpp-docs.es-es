---
title: Error irrecuperable C1092 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8f5b5d903fe1fb2d3182a7b08f7bf82ddf334fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1092"></a>Error irrecuperable C1092
La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación  
  
 Ha cambiado o agregado un tipo de datos desde la última compilación correcta.  
  
-   Editar y continuar no admite cambios en los tipos de datos existentes, incluidas las definiciones de clase, estructura o enumeración. Debe detener la depuración y compilar la aplicación.  
  
-   Editar y continuar no admite la adición de nuevos tipos de datos si un archivo de base de datos de programa, como vc*x*0.pdb (donde *x* es la versión principal de Visual C++ en uso) es de solo lectura. Para agregar tipos de datos, el compilador debe abrir el archivo .pdb en modo de escritura.  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Para quitar este error sin tener que terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar** , elija **Aplicar cambios en el código**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente  
  
1.  En el menú **Depurar** , elija **Detener depuración**.  
  
2.  En el menú **Compilar** , elija **Compilar**.  
  
 Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).