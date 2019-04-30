---
title: Error de BSCMAKE BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380531"
---
# <a name="bscmake-error-bk1517"></a>Error de BSCMAKE BK1517

archivo de código fuente para archivo .sbr compilado con /Yc e /Yu

El archivo .sbr hace referencia a sí mismo. Probablemente se recompila con /Yu después de compilar con/Yc. Restablecer la opción del compilador para el archivo de origen/Yc, a continuación, seleccione **recompilar** para generar los nuevos archivos. sbr. No se vuelva a compilar el archivo de código fuente con /Yu.