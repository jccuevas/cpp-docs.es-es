---
title: Error del evaluador de expresiones CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195518"
---
# <a name="expression-evaluator-error-cxx0033"></a>Error del evaluador de expresiones CXX0033

error en la información de tipo OMF

El archivo ejecutable no tenía un formato de módulo de objeto válido (OMF) para la depuración.

Este error es idéntico a CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El archivo ejecutable no se creó con el vinculador lanzado con esta versión de Visual C++. Volver a vincular el código objeto mediante la versión actual de LINK. exe.

1. Es posible que el archivo. exe se haya dañado. Vuelva a compilar y vincular el programa.
