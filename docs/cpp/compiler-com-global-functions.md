---
title: Funciones globales COM del compilador | Documentos de Microsoft
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
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
caps.latest.revision: 7
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 28755b770594209d22de0ae6ac35323ebf61e109
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="compiler-com-global-functions"></a>Funciones globales COM de compilador
**Específicos de Microsoft**  
  
 Están disponibles las siguientes rutinas:  
  
|Función|Descripción|  
|--------------|-----------------|  
|[_com_raise_error](../cpp/com-raise-error.md)|Produce una [_com_error](../cpp/com-error-class.md) en respuesta a un error.|  
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Reemplaza la función predeterminada que se utiliza para el control de errores de COM.|  
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convierte un `BSTR` valor a un **char \* **.|  
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convierte un **char \* ** valor a un `BSTR`.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)
