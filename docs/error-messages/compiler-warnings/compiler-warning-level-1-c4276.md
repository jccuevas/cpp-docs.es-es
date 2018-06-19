---
title: Compilador advertencia (nivel 1) C4276 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afedab27c2fb93075aa33053c12ec6973824f144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277311"
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276
'función': no se ha proporcionado prototipo; no supone ningún parámetro  
  
 Al tomar la dirección de una función con el [__stdcall](../../cpp/stdcall.md) convención de llamada, se debe indicar un prototipo para el compilador pueda crear el nombre representativo de la función. Puesto que *función* no tiene prototipo, el compilador, al crear el nombre representativo, supone que la función no tiene ningún parámetro.