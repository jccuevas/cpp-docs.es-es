---
title: _bstr_t (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7cb3d05997cfe3d803f522962ed9e7382269bd3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404930"
---
# <a name="bstrt-class"></a>_bstr_t (Clase)
**Específicos de Microsoft**  
  
 Un `_bstr_t` objeto encapsula el [tipo de datos BSTR](http://msdn.microsoft.com/1b2d7d2c-47af-4389-a6b6-b01b7e915228). La clase administra la asignación de recursos y la desasignación con llamadas de función `SysAllocString` y `SysFreeString` y otros `BSTR` API cuando corresponda. El **_bstr_t** clase utiliza el recuento de referencias para evitar una sobrecarga excesiva.  
  
### <a name="construction"></a>Construcción  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Construye un objeto `_bstr_t`.|  
  
### <a name="operations"></a>Operaciones  
  
|||  
|-|-|  
|[Asignar](../cpp/bstr-t-assign.md)|Copia un valor `BSTR` en el valor `BSTR` contenido en `_bstr_t`.|  
|[Asociar](../cpp/bstr-t-attach.md)|Vincula un contenedor `_bstr_t` a un `BSTR`.|  
|[copy](../cpp/bstr-t-copy.md)|Crea una copia del objeto `BSTR` encapsulado.|  
|[Desasociar](../cpp/bstr-t-detach.md)|Devuelve el `BSTR` contenido en `_bstr_t` y desasocia `BSTR` de `_bstr_t`.|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|Apunta al `BSTR` contenido en `_bstr_t`.|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Señala al principio del objeto `BSTR` incluido en `_bstr_t`.|  
|[length](../cpp/bstr-t-length.md)|Devuelve el número de caracteres de `_bstr_t`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../cpp/bstr-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_bstr_t` existente.|  
|[operator +=](../cpp/bstr-t-operator-add-equal-plus.md)|Agrega caracteres al final del objeto `_bstr_t`.|  
|[operador +](../cpp/bstr-t-operator-add-equal-plus.md)|Concatena dos cadenas.|  
|[operador !](../cpp/bstr-t-operator-logical-not.md)|Comprueba si encapsulado `BSTR` es una cadena NULL.|  
|[operador ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Compara dos objetos `_bstr_t`.|  
|[operador wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrae los punteros al objeto `BSTR` multibyte o Unicode encapsulado.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comutil.h >  
  
 **Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)