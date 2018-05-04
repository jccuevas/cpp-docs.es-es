---
title: _variant_t (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebe850e4b0d0d9fd352df0e60c4ea0737b9fd8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="variantt-class"></a>_variant_t (Clase)
**Específicos de Microsoft**  
  
 Un objeto `_variant_t` encapsula el tipo de datos `VARIANT`. La clase administra la asignación de recursos y desasignación y realiza llamadas de función a **VariantInit** y **VariantClear** según corresponda.  
  
### <a name="construction"></a>Construcción  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|Construye un objeto `_variant_t`.|  
  
### <a name="operations"></a>Operaciones  
  
|||  
|-|-|  
|[Asociar](../cpp/variant-t-attach.md)|Asocia un **VARIANT** objeto en el `_variant_t` objeto.|  
|[Borrar](../cpp/variant-t-clear.md)|Borra el objeto encapsulado **VARIANT** objeto.|  
|[ChangeType](../cpp/variant-t-changetype.md)|Cambia el tipo de la `_variant_t` objeto para el functoid **VARTYPE**.|  
|[Desasociar](../cpp/variant-t-detach.md)|Desasocia el objeto encapsulado **VARIANT** objeto desde este `_variant_t` objeto.|  
|[setString](../cpp/variant-t-setstring.md)|Asigna una cadena a este objeto `_variant_t`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../cpp/variant-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_variant_t` existente.|  
|[operador ==,! =](../cpp/variant-t-relational-operators.md)|Compara dos objetos `_variant_t` para ver si son iguales o no.|  
|[Extractores de datos](../cpp/variant-t-extractors.md)|Extraer datos de encapsulado **VARIANT** objeto.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comutil.h >  
  
 **Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)