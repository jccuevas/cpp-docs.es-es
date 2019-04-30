---
title: Error del evaluador de expresiones CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397060"
---
# <a name="expression-evaluator-error-cxx0033"></a>Error del evaluador de expresiones CXX0033

Error en la información de tipo OMF

El archivo ejecutable no tenía un formato de módulo de objeto válido (OMF) para la depuración.

Este error es idéntico a CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El archivo ejecutable no se creó con el vinculador que se suministra con esta versión de Visual C++. Volver a vincular el código de objeto con la versión actual de LINK.exe.

1. El archivo .exe esté dañado. Vuelva a compilar y volver a vincular el programa.