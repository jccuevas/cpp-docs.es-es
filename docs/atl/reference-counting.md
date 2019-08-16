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
ms.openlocfilehash: 565b74956280d4e80c41376ead4249e69980a80e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492219"
---
# <a name="reference-counting"></a>Recuento de referencias

COM no intenta automáticamente quitar un objeto de la memoria cuando considera que el objeto ya no se utiliza. En su lugar, el programador de objetos debe quitar el objeto no utilizado. El programador determina si un objeto se puede quitar en función de un recuento de referencias.

COM utiliza los `IUnknown` métodos, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), para administrar el recuento de referencias de interfaces en un objeto. Las reglas generales para llamar a estos métodos son:

- Siempre que un cliente recibe un puntero de `AddRef` interfaz, se debe llamar a en la interfaz.

- Cada vez que el cliente ha terminado de usar el puntero de interfaz `Release`, debe llamar a.

En una implementación simple, cada `AddRef` llamada incrementa y cada `Release` llamada reduce una variable de contador dentro del objeto. Cuando el recuento vuelve a cero, la interfaz ya no tiene usuarios y es libre de quitarse de la memoria.

También se puede implementar el recuento de referencias para que se cuente cada referencia al objeto (no a una interfaz individual). En este caso, cada `AddRef` y `Release` llama a los delegados de una implementación central en `Release` el objeto y libera todo el objeto cuando su recuento de referencias llega a cero.

> [!NOTE]
>  Cuando un `CComObject`objeto derivado de se construye mediante el operador **New** , el recuento de referencias es 0. Por lo tanto, se `AddRef` debe realizar una llamada a después de `CComObject`crear correctamente el objeto derivado de.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Administrar la duración de los objetos mediante el recuento de referencias](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
