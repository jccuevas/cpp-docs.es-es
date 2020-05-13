---
title: Error grave de NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193685"
---
# <a name="nmake-fatal-error-u1051"></a>Error grave de NMAKE U1051

memoria insuficiente

NMAKE se quedó sin memoria, incluida la memoria virtual, porque el archivo make era demasiado grande o complejo.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Libere espacio en disco.

1. Aumente el tamaño del archivo de paginación de Windows NT o del archivo de intercambio de Windows.

1. Si solo se usa una parte del archivo make, divida el archivo make en archivos independientes o use **! Si** las directivas de preprocesamiento limitan la cantidad que NMAKE debe procesar. El  **Si** las directivas incluyen **! Si**es, `!IFDEF`, **! IFNDEF**, **! en caso contrario**, **! ELSE** `IFDEF`y **!** En caso contrario `IFNDEF`.
