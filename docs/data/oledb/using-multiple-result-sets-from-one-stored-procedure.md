---
title: Utilizar varios conjuntos de resultados de un procedimiento almacenado
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209292"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilizar varios conjuntos de resultados de un procedimiento almacenado

La mayoría de los procedimientos almacenados devuelven varios conjuntos de resultados. Este procedimiento almacenado normalmente incluye una o varias instrucciones SELECT. El consumidor debe considerar esta inclusión para controlar todos los conjuntos de resultados.

## <a name="to-handle-multiple-result-sets"></a>Para controlar varios conjuntos de resultados

1. Cree una clase de `CCommand` con `CMultipleResults` como un argumento de plantilla y con el descriptor de acceso de su elección, normalmente un descriptor de acceso dinámico o manual. Si usa otro tipo de descriptor de acceso, es posible que no pueda determinar las columnas de salida para cada conjunto de filas.

1. Ejecute el procedimiento almacenado como de costumbre y enlace las columnas (vea [¿cómo se capturan los datos?](../../data/oledb/fetching-data.md)).

1. Use los datos.

1. Llame a `GetNextResult` en la clase `CCommand`. Si hay otro conjunto de filas de resultados disponible, `GetNextResult` Devuelve S_OK y debe volver a enlazar las columnas si usa un descriptor de acceso manual. Si `GetNextResult` devuelve un error, no hay más conjuntos de resultados disponibles.

## <a name="see-also"></a>Consulte también

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)
