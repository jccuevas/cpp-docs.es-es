---
title: 'Administración de memoria: Marco asignación | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 264a3b5618b1c153219d5dee838af38bd7f49f49
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931065"
---
# <a name="memory-management-frame-allocation"></a>Administración de memoria: asignación de marcos
Asignación en el marco toma su nombre de la "marco de pila" que se establece cada vez que se invoque una función. El marco de pila es un área de memoria que contiene de forma temporal los argumentos para la función, así como las variables que se definen locales para la función. Variables de marco a menudo se denominan "variables"automáticas"porque el compilador asigna automáticamente el espacio para ellos.  
  
 Hay dos características clave de asignación en el marco. En primer lugar, cuando se define una variable local, se asigna suficiente espacio en el marco de pila para contener la variable completa, incluso si es una matriz de gran tamaño o una estructura de datos. En segundo lugar, las variables de marco se eliminan automáticamente cuando salen del ámbito:  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]  
  
 Para las variables de función local, esta transición de ámbito se produce cuando la función se cierra, pero el ámbito de una variable de marco puede ser menor que una función si se utilizan llaves anidadas. Esta eliminación automática de variables de marco es muy importante. En el caso de tipos primitivos simples (como **int** o **bytes**), matrices o estructuras de datos, la eliminación automática simplemente reclama la memoria utilizada por la variable. Puesto que la variable ha salido del ámbito, no puede obtenerse todos modos. Sin embargo, en el caso de objetos de C++, el proceso de eliminación automática es un poco más complicado.  
  
 Cuando un objeto se define como una variable de marco, se invoca automáticamente su constructor en el punto donde se encuentra la definición. Cuando el objeto se sale del ámbito, su destructor se invoca automáticamente antes de la memoria para el objeto se recupera. Esta construcción y destrucción automáticas pueden resultar muy útiles, pero debe ser consciente de las llamadas automáticas, especialmente al destructor.  
  
 La principal ventaja de asignar objetos en el marco es que se eliminen automáticamente. Cuando se asignan los objetos en el marco, no tiene que preocuparse sobre los objetos olvidados provocando pérdidas de memoria. (Para obtener detalles sobre las pérdidas de memoria, vea el artículo [detectar pérdidas de memoria en MFC](http://msdn.microsoft.com/en-us/29ee8909-96e9-4246-9332-d3a8aa8d4658).) Una desventaja de asignación en el marco es que no se puede usar variables de marco fuera de su ámbito. Otro factor para elegir la asignación en el marco frente a asignación en el montón es que para grandes estructuras y objetos, a menudo es mejor usar el montón en lugar de la pila para el almacenamiento ya que el espacio de pila es limitado.  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria](../mfc/memory-management.md)

