---
title: Inicializar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0e970d6e8a166283f82575b309cf023f48899403
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626350"
---
# <a name="initializing-documents-and-views"></a>Inicializar documentos y vistas

Los documentos se crean de dos maneras diferentes, por lo que la clase de documento debe admitir ambas maneras. En primer lugar, el usuario puede crear un nuevo documento vacío con el comando archivo nuevo. En ese caso, inicialice el documento en la invalidación de la función miembro [OnNewDocument](reference/cdocument-class.md#onnewdocument) de la clase [CDocument](reference/cdocument-class.md). En segundo lugar, el usuario puede usar el comando abrir del menú Archivo para crear un nuevo documento cuyo contenido se lea desde un archivo. En ese caso, inicialice el documento en la invalidación de la función miembro [OnOpenDocument](reference/cdocument-class.md#onopendocument) de la clase `CDocument` . Si ambas inicializaciones son iguales, puede llamar a una función miembro común desde ambas invalidaciones o `OnOpenDocument` puede llamar `OnNewDocument` a para inicializar un documento limpio y después finalizar la operación de apertura.

Las vistas se crean una vez creados los documentos. El mejor momento para inicializar una vista es después de que el marco haya terminado de crear el documento, la ventana de marco y la vista. Puede inicializar la vista invalidando la función miembro [OnInitialUpdate](reference/cview-class.md#oninitialupdate) de [CView](reference/cview-class.md). Si necesita reinicializar o ajustar nada cada vez que cambie el documento, puede invalidar [Actualizar](reference/cview-class.md#onupdate).

## <a name="see-also"></a>Consulte también

[Inicialización y limpieza de documentos y vistas](initializing-and-cleaning-up-documents-and-views.md)
