---
title: no_injected_text | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74336ffaa5e1f9f1990acedf1669526c9152b82b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880353"
---
# <a name="noinjectedtext"></a>no_injected_text
Evita que el compilador inserte código como resultado del uso de atributos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 `boolean`(opcional)  
 **True** si no desea que ningún código insertado, **false** para permitir que el código insertar. **True** es el valor predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 El uso más común de la **no_injected_text** atributo de C++ es la [/Fx](../build/reference/fx-merge-injected-code.md) opción del compilador, que inserta la **no_injected_text** atributo en el archivo .mrg.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
