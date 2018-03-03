---
title: Naked (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 474cb57ced17088c0ce9be8613a9373c702afe69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="naked-c"></a>Naked (C)
**Específicos de Microsoft**  
  
 El atributo de clase de almacenamiento naked es una extensión específica de Microsoft para el lenguaje C. El compilador genera código sin código de prólogo y epílogo para las funciones declaradas con el atributo de clase de almacenamiento naked. Las funciones naked son útiles cuando se necesita escribir secuencias de código de prólogo/epílogo propias mediante código ensamblador alineado. Las funciones naked son útiles para escribir controladores de dispositivos virtuales.  
  
 Para obtener información concreta sobre cómo se usa el atributo naked, vea [Funciones naked](../c-language/naked-functions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)