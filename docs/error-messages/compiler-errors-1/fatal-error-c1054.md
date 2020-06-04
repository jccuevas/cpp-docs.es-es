---
title: Error irrecuperable C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204469"
---
# <a name="fatal-error-c1054"></a>Error irrecuperable C1054

límite del compilador: los inicializadores están demasiado anidados

El código supera el límite de anidamiento de los inicializadores (10-15 niveles, en función de la combinación de tipos que se van a inicializar).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Simplifique los tipos de datos que se van a inicializar para reducir el anidamiento.

1. Inicialice las variables en instrucciones independientes después de la declaración.
