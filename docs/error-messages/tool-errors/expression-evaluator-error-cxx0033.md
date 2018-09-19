---
title: Error del evaluador de expresiones CXX0033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f37b53c30d36a43d339132bfd9baca3e5ec70c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057204"
---
# <a name="expression-evaluator-error-cxx0033"></a>Error del evaluador de expresiones CXX0033

Error en la información de tipo OMF

El archivo ejecutable no tenía un formato de módulo de objeto válido (OMF) para la depuración.

Este error es idéntico a CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El archivo ejecutable no se creó con el vinculador que se suministra con esta versión de Visual C++. Volver a vincular el código de objeto con la versión actual de LINK.exe.

1. El archivo .exe esté dañado. Vuelva a compilar y volver a vincular el programa.