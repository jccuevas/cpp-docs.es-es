---
title: Acceso a miembros | Documentos de Microsoft
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
- member-selection operators
- pointers, smart
- member access, overloaded operators
- operator overloading, member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: 9
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
ms.openlocfilehash: 21cdc3de990a8b23645bb09f9f093fb0f2498254
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="member-access"></a>Acceso a miembros
Acceso a miembros de clase puede controlarse mediante la sobrecarga el operador de acceso de miembro (**->**). Este operador se considera un operador unario en este uso, y la función de operador sobrecargado debe ser una función miembro de clase. Por lo tanto, la declaración de una función de ese tipo es:  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
class-type *operator->()  
```  
  
## <a name="remarks"></a>Comentarios  
 donde *tipo de clase* es el nombre de la clase a la que pertenece este operador. La función de operador de acceso a miembros debe ser una función miembro no estática.  
  
 Este operador se usa (a menudo junto con el operador de desreferenciación de puntero) para implementar "punteros inteligentes" que validan punteros antes del uso de desreferenciación o de recuento.  
  
 El elemento de lenguaje **.** no se pueden sobrecargar el operador de acceso de miembro.  
  
## <a name="see-also"></a>Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)
