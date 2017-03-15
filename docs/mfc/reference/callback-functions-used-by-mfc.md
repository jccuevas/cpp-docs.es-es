---
title: "Funciones de devolución de llamada usadas por MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions, MFC
- MFC, callback functions
- functions [C++], callback
- callback functions
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b4d104fa76347da43c84611672f843511f0f3725
ms.lasthandoff: 02/24/2017

---
# <a name="callback-functions-used-by-mfc"></a>Funciones de devolución de llamada usadas por MFC
Tres funciones de devolución de llamada aparecen en la biblioteca Microsoft Foundation Class. Una descripción de las funciones de devolución de llamada que se pasan a [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring), y [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc) sigue a este tema. Para el uso general de las funciones de devolución de llamada, vea la sección Comentarios de estas funciones miembro. Tenga en cuenta que todas las funciones de devolución de llamada deben capturar excepciones de MFC antes de volver a Windows, puesto que no se producirán excepciones en los límites de la devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


