---
title: Advertencia de la línea de comandos D9026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07be633e56dad6c8f0b304a3c88c1b9919221d4a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079159"
---
# <a name="command-line-warning-d9026"></a>Advertencia de la línea de comandos D9026

las opciones se aplican a toda la línea de comandos

Se especificó una opción en un comando después de que se especificó un nombre de archivo. La opción se aplica al archivo que le precede.

Por ejemplo, en el comando

```
CL verdi.c /G5 puccini.c
```

el archivo VERDI.c se compilará con la opción/G5, el valor predeterminado de no/G4.

Este comportamiento es diferente de algunas versiones anteriores, que se aplican solo las opciones especificadas antes el nombre de archivo, lo que resulta en VERDI.c que se compiló con/G4 y PUCCINI.c que se está compilando mediante/G5.