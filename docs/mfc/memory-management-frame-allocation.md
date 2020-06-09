---
title: 'Administración de memoria: asignación de marcos'
ms.date: 11/04/2016
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
ms.openlocfilehash: 1ecf1c08164d1a760fce62457a6019e767ed2605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626301"
---
# <a name="memory-management-frame-allocation"></a>Administración de memoria: asignación de marcos

La asignación en el marco toma su nombre del "marco de pila" que se configura cada vez que se llama a una función. El marco de pila es un área de memoria que contiene temporalmente los argumentos para la función, así como todas las variables que se definen de forma local en la función. Las variables de marco se suelen denominar variables "automáticas", ya que el compilador asigna automáticamente el espacio para ellas.

Hay dos características clave de las asignaciones de Marcos. En primer lugar, al definir una variable local, se asigna espacio suficiente en el marco de pila para que contenga toda la variable, aunque sea una matriz grande o una estructura de datos. En segundo lugar, las variables de marco se eliminan automáticamente cuando salen del ámbito:

[!code-cpp[NVC_MFC_Utilities#10](codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

En el caso de las variables de función local, esta transición de ámbito se produce cuando finaliza la función, pero el ámbito de una variable de marco puede ser menor que una función si se usan llaves anidadas. Esta eliminación automática de las variables de marco es muy importante. En el caso de los tipos primitivos simples (como **int** o **byte**), matrices o estructuras de datos, la eliminación automática simplemente recupera la memoria usada por la variable. Dado que la variable ha salido del ámbito, no se puede tener acceso a ella de todos modos. Sin embargo, en el caso de los objetos de C++, el proceso de eliminación automática es un poco más complicado.

Cuando un objeto se define como una variable de marco, su constructor se invoca automáticamente en el punto en el que se encuentra la definición. Cuando el objeto sale del ámbito, su Destructor se invoca automáticamente antes de que se recupere la memoria para el objeto. Esta construcción y destrucción automáticas pueden ser muy útiles, pero debe tener en cuenta las llamadas automáticas, especialmente en el destructor.

La principal ventaja de asignar objetos en el marco es que se eliminan automáticamente. Cuando se asignan los objetos en el marco, no es necesario preocuparse por los objetos olvidados que causan pérdidas de memoria. (Para obtener más información sobre las pérdidas de memoria, vea el artículo [detectar pérdidas de memoria en MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100))). Una desventaja de la asignación de fotogramas es que las variables de marco no se pueden usar fuera de su ámbito. Otro factor en la elección de la asignación de marcos frente a la asignación del montón es que para estructuras y objetos grandes, a menudo es mejor usar el montón en lugar de la pila para el almacenamiento, ya que el espacio de pila suele estar limitado.

## <a name="see-also"></a>Consulte también

[Administración de memoria](memory-management.md)
