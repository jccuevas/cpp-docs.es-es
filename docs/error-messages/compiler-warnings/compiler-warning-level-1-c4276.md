---
title: Compilador advertencia (nivel 1) C4276 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af9a32da86a0ea9e530af03a2175976d4cd9f091
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276
'función': no se ha proporcionado prototipo; no supone ningún parámetro  
  
 Al tomar la dirección de una función con el [__stdcall](../../cpp/stdcall.md) convención de llamada, se debe indicar un prototipo para el compilador pueda crear el nombre representativo de la función. Puesto que *función* no tiene prototipo, el compilador, al crear el nombre representativo, supone que la función no tiene ningún parámetro.