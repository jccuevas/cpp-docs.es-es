---
title: nonextensible (atributo)
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257636"
---
# <a name="nonextensible-attribute"></a>nonextensible (atributo)

Si no se extiende una interfaz dual en tiempo de ejecución (es decir, si no se ofrecen métodos ni propiedades a través de `IDispatch::Invoke` que no están disponibles a través de la tabla vtable), debe aplicar el **nonextensible** atributo a la interfaz definición. Este atributo proporciona información para los idiomas de cliente (como Visual Basic) que se puede usar para habilitar la comprobación de código completo en tiempo de compilación. Si no se proporciona este atributo, los errores pueden permanecer ocultos en el código de cliente hasta el tiempo de ejecución.

Para obtener más información sobre la **nonextensible** atributo y un ejemplo, vea [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Vea también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)
