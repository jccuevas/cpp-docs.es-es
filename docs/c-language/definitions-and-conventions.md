---
title: Definiciones y convenciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74a29acfcdc58b068ebabe9bc1c9b033cf801c21
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760411"
---
# <a name="definitions-and-conventions"></a>Definiciones y convenciones
Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.  
  
Los marcadores de posición de la sintaxis son no terminales y se definen en otras partes de este resumen de la sintaxis. Las definiciones pueden ser recursivas.  
  
Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo,  
  
> **{** *expression*<sub>opt</sub> **}**
  
indica una expresión opcional encerrada entre llaves.  
  
Las convenciones de sintaxis utilizan diferentes atributos de fuente para los distintos componentes de la sintaxis. Los símbolos y fuentes son los siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|*elemento no terminal*|La cursiva indica elementos no terminales.|  
|**const**|Los elementos terminales en negrita son símbolos y palabras literales reservadas que deben especificarse tal como aparecen. Los caracteres en este contexto siempre distinguen entre mayúsculas y minúsculas.|  
|<sub>opt</sub>|Los elementos no terminales seguidos de <sub>opt</sub> son siempre opcionales.|  
|tipo de letra predeterminado|Los caracteres del conjunto descrito o enumerado con este tipo de fuente se pueden usar como terminales en las instrucciones de C.|  
  
Un signo de dos puntos (**:**) a continuación de un no terminal presenta su definición. Las definiciones alternativas se enumeran en líneas independientes, excepto si van precedidas de las palabras "uno de".  
  
## <a name="see-also"></a>Vea también  
[Resumen de la sintaxis de lenguaje C](../c-language/c-language-syntax-summary.md)