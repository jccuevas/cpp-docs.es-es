---
title: Clases base
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 50bddef3ea1ee1462d8cf115c0980270c8deab25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181478"
---
# <a name="base-classes"></a>Clases base

El proceso de herencia crea una nueva clase derivada que se compone de los miembros de la clase o clases base más cualquier nuevo miembro agregado por la clase derivada. En una herencia múltiple, es posible crear un gráfico de herencia donde la misma clase base forme parte de varias de las clases derivadas. En la ilustración siguiente se muestra este tipo de gráfico.

![Varias instancias de una clase base](../cpp/media/vc38xn1.gif "Varias instancias de una clase base") <br/>
Varias instancias de una clase base única

En la ilustración, se muestran las representaciones gráficas de los componentes de `CollectibleString` y `CollectibleSortable`. Sin embargo, la clase base, `Collectible`, está en `CollectibleSortableString` a través de la ruta de `CollectibleString` y la ruta de `CollectibleSortable`. Para eliminar esta redundancia, estas clases se pueden declarar como clases base virtuales cuando se heredan.
