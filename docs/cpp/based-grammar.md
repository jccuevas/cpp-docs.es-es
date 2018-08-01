---
title: gramática __based | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d1713b0cc8e1d5d53d3b30f3dd48a0b54a3782
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401966"
---
# <a name="based-grammar"></a>Gramática __based
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El direccionamiento de base es útil cuando se necesita el control preciso del segmento en el que se asignan los objetos (datos basados estáticos y dinámicos).  
  
 La única forma de direccionamiento de base aceptable en compilaciones de 32 bits y 64 bits es "basado en un puntero" que define un tipo que contiene un desplazamiento de 32 bits o 64 bits a una base de 32 bits o 64 bits o basado en **void**.  
  
## <a name="grammar"></a>Gramática  
 *modificador de intervalo en función*:  
 **__based (***base expresión***)**   
  
 *expresión base*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-CAST*  
  
 *en función de variable*:  
 *identifier*  
  
 *en función-abstract-declarator*:  
 *abstract-declarator*  
  
 *tipo base*:  
 *nombre de tipo*  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Punteros con base](../cpp/based-pointers-cpp.md)