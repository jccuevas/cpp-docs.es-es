---
title: "gramática __based | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 427906751c57b8b5f0c46479e8481394fa20f56c
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="based-grammar"></a>Gramática __based
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El direccionamiento de base es útil cuando se necesita el control preciso del segmento en el que se asignan los objetos (datos basados estáticos y dinámicos).  
  
 La única forma de direccionamiento de base aceptable en compilaciones de 32 bits y 64 bits es "basado en un puntero" que define un tipo que contiene un desplazamiento de 32 bits o de 64 bits respecto a una base de 32 bits o de 64 bits, o basado en `void`.  
  
## <a name="grammar"></a>Gramática  
 *modificador de intervalo según*:  
 **__based (***base-expression***)    **  
  
 *expresión base*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-CAST*  
  
 *variable según*:  
 *identifier*  
  
 *declarador abstracto según*:  
 *abstract-declarator*  
  
 *tipo base*:  
 *nombre de tipo*  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Punteros con base](../cpp/based-pointers-cpp.md)
