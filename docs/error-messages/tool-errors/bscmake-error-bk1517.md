---
title: Error de BSCMAKE BK1517 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 941773fbcf65a3b1c1a6041a1e7a067cfc286823
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097060"
---
# <a name="bscmake-error-bk1517"></a>Error de BSCMAKE BK1517

archivo de código fuente para archivo .sbr compilado con /Yc e /Yu

El archivo .sbr hace referencia a sí mismo. Probablemente se recompila con /Yu después de compilar con/Yc. Restablecer la opción del compilador para el archivo de origen/Yc, a continuación, seleccione **recompilar** para generar los nuevos archivos. sbr. No se vuelva a compilar el archivo de código fuente con /Yu.