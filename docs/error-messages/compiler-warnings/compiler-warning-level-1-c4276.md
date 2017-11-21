---
title: Compilador advertencia (nivel 1) C4276 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4276
dev_langs: C++
helpviewer_keywords: C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 609acf714cc149d7a12d515b991fa78c40244129
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276
'función': no se ha proporcionado prototipo; no supone ningún parámetro  
  
 Al tomar la dirección de una función con el [__stdcall](../../cpp/stdcall.md) convención de llamada, se debe indicar un prototipo para el compilador pueda crear el nombre representativo de la función. Puesto que *función* no tiene prototipo, el compilador, al crear el nombre representativo, supone que la función no tiene ningún parámetro.