---
title: Naked (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2aa9ba1d3e6397a35389c2ee46ab30f19c0e6227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="naked-c"></a>Naked (C)
**Específicos de Microsoft**  
  
 El atributo de clase de almacenamiento naked es una extensión específica de Microsoft para el lenguaje C. El compilador genera código sin código de prólogo y epílogo para las funciones declaradas con el atributo de clase de almacenamiento naked. Las funciones naked son útiles cuando se necesita escribir secuencias de código de prólogo/epílogo propias mediante código ensamblador alineado. Las funciones naked son útiles para escribir controladores de dispositivos virtuales.  
  
 Para obtener información concreta sobre cómo se usa el atributo naked, vea [Funciones naked](../c-language/naked-functions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)