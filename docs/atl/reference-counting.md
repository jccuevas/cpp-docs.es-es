---
title: Recuento de referencias (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321741"
---
# <a name="reference-counting"></a>Recuento de referencias

COM en sí no intenta eliminar automáticamente un objeto de la memoria cuando piensa que el objeto ya no se está utilizando. En su lugar, el programador de objetos debe quitar el objeto no utilizado. El programador determina si un objeto se puede quitar en función de un recuento de referencias.

COM utiliza `IUnknown` los métodos [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), para administrar el recuento de referencias de interfaces en un objeto. Las reglas generales para llamar a estos métodos son:

- Siempre que un cliente recibe `AddRef` un puntero de interfaz, se debe llamar en la interfaz.

- Siempre que el cliente haya terminado de `Release`usar el puntero de interfaz, debe llamar a .

En una implementación `AddRef` simple, cada `Release` llamada aumenta y cada llamada disminuye una variable de contador dentro del objeto. Cuando el recuento vuelve a cero, la interfaz ya no tiene ningún usuario y es libre de quitarse de la memoria.

El recuento de referencias también se puede implementar para que se cuente cada referencia al objeto (no a una interfaz individual). En este caso, cada `AddRef` y `Release` llamar a delegados `Release` a una implementación central en el objeto y libera todo el objeto cuando su recuento de referencias llega a cero.

> [!NOTE]
> Cuando `CComObject`se construye un objeto derivado mediante el operador **new,** el recuento de referencias es 0. Por lo tanto, se debe realizar una llamada después `AddRef` de crear correctamente el `CComObject`objeto derivado.

## <a name="see-also"></a>Consulte también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Administración de la duración de los objetos a través del recuento de referencias](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
