---
title: Importar y exportar funciones Inline | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6f8d159a1537cdfee02d45805632ba9ad4afa7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting-inline-functions"></a>Importar y exportar funciones inline
Las funciones importadas se pueden definir como alineada. El efecto es aproximadamente el mismo que definir una función estándar inline; llamadas a la función se expanden a código en línea, como una macro. Esto es especialmente útil como una manera de admitir C++ las clases en un archivo DLL que puede incluir en línea algunas de su funciones miembro para mejorar la eficacia.  
  
 Una característica de una función inline importada es que puede tomar su dirección en C++. El compilador devuelve la dirección de la copia de la función insertada que residen en el archivo DLL. Otra característica de las funciones inline importadas es que puede inicializar datos locales estáticos de la función importada, a diferencia de los datos globales importados.  
  
> [!CAUTION]
>  Debe tener cuidado al proporcionar funciones inline importadas, ya que podrían producir la posibilidad de conflictos de versiones. Una función inline se expande para crear el código de aplicación; por lo tanto, si más adelante vuelve a escribir la función, se no se actualiza a menos que se vuelva a compilar la aplicación en Sí. (Normalmente, las funciones DLL pueden actualizarse sin volver a generar las aplicaciones que las utilizan.)  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)