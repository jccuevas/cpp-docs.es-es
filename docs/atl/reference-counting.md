---
title: Referencia de recuento (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: fa160cb40af632321e1b14fd3ca88a4dd578b972
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293438"
---
# <a name="reference-counting"></a>Recuento de referencias

El propio COM no automáticamente intenta quitar un objeto de memoria cuando piensa que el objeto ya no está usando. En su lugar, el programador de objetos debe quitar el objeto sin usar. El programador determina si un objeto se puede quitar según un recuento de referencias.

COM utiliza el `IUnknown` métodos, [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) y [versión](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), para administrar el recuento de referencias de las interfaces en un objeto. Las reglas generales para llamar a estos métodos son:

- Cada vez que un cliente recibe un puntero de interfaz `AddRef` debe llamarse en la interfaz.

- Cada vez que el cliente ha terminado de utilizar el puntero de interfaz, debe llamar a `Release`.

En una implementación simple, cada `AddRef` llamar a incrementos y cada `Release` llamar reduce una variable de contador dentro del objeto. Cuando el recuento vuelve a cero, la interfaz ya no tiene ningún usuario y es gratuita para quitarse de la memoria.

Recuento de referencias también se puede implementar para que se cuentan todas las referencias al objeto (no a una interfaz individual). En este caso, cada `AddRef` y `Release` llamar a los delegados en una implementación central del objeto, y `Release` libera el objeto completo cuando su recuento de referencias llega a cero.

> [!NOTE]
>  Cuando un `CComObject`-derivado objeto se construye utilizando el **nuevo** operador, el recuento de referencias es 0. Por lo tanto, una llamada a `AddRef` se deben realizar después de crear correctamente el `CComObject`-objeto derivado.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Administrar la duración de objeto a través de un recuento de referencias](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)
