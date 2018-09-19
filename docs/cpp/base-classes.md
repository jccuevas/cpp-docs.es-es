---
title: Las clases base | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6d6494cc1ef371cfeb51647bc310a74ac68bfb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059217"
---
# <a name="base-classes"></a>Clases base

El proceso de herencia crea una nueva clase derivada que se compone de los miembros de la clase o clases base más cualquier nuevo miembro agregado por la clase derivada. En una herencia múltiple, es posible crear un gráfico de herencia donde la misma clase base forme parte de varias de las clases derivadas. En la ilustración siguiente se muestra este tipo de gráfico.

![Varias instancias de una clase base](../cpp/media/vc38xn1.gif "vc38XN1") varias instancias de una única clase Base

En la ilustración, se muestran las representaciones gráficas de los componentes de `CollectibleString` y `CollectibleSortable`. Sin embargo, la clase base, `Collectible`, está en `CollectibleSortableString` a través de la ruta de `CollectibleString` y la ruta de `CollectibleSortable`. Para eliminar esta redundancia, estas clases se pueden declarar como clases base virtuales cuando se heredan.