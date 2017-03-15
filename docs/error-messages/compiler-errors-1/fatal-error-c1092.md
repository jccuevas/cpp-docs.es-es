---
title: Error grave C1092 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 6d93fd662b638126e21d5f5f034138c0e6f0e0ad
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1092"></a>Error irrecuperable C1092
La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación  
  
 Cambiar o agregar un tipo de datos desde la última compilación correcta.  
  
-   Editar y continuar no admite cambios en los tipos de datos existentes, incluidas las definiciones de clase, estructura o enumeración. Debe detener la depuración y compilar la aplicación.  
  
-   Editar y continuar no admite la adición de nuevos tipos de datos si un archivo de base de datos de programa, como vc*x*0.pdb (donde *x* es la versión principal de Visual C++ en uso) es de sólo lectura. Para agregar tipos de datos, el compilador debe abrir el archivo .pdb en modo de escritura.  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Para quitar este error sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar** , elija **Aplicar cambios en el código**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente  
  
1.  En el menú **Depurar** , elija **Detener depuración**.  
  
2.  En el menú **Compilar** , elija **Compilar**.  
  
 Para obtener más información, consulte el [cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).
