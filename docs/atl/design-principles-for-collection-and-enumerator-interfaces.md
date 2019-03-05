---
title: Diseño de Interfaces de enumerador (ATL) y de colección
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: f40c86d3bc8d9b4e4c752fe6657f6a5a14f19e0c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269942"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principios de diseño para la recopilación y las Interfaces de enumerador

Hay diferentes principios de cada tipo de interfaz de diseño:

- Proporciona una interfaz de colección *aleatorio* el acceso a un *único* elemento de la colección a través de la `Item` método, permite a los clientes descubrir cuántos elementos se encuentran en la colección a través de la `Count` propiedad, y a menudo permite a los clientes agregar y quitar elementos.

- Proporciona una interfaz de enumerador *serie* el acceso a *varios* elementos de una colección, no permite descubrir cuántos elementos están en la colección (hasta que el enumerador deja de devolver al cliente elementos), y no proporciona ninguna manera de agregar o quitar elementos.

Cada tipo de interfaz desempeña un rol diferente al proporcionar acceso a los elementos de una colección.

## <a name="see-also"></a>Vea también

[Las colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)
