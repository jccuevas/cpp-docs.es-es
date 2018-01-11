---
title: usesgetlasterror | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.usesgetlasterror
dev_langs: C++
helpviewer_keywords: usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05c74f1254230270654b3dc0b44f541e4fe9ef2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="usesgetlasterror"></a>usesgetlasterror
Indica que el llamador que si se produce un error al llamar a esa función, a continuación, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[usesgetlasterror]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **usesgetlasterror** atributo C++ tiene la misma funcionalidad que la [usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Consulte la [idl_module](../windows/idl-module.md) ejemplo para obtener un ejemplo de cómo usar **usesgetlasterror**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**módulo** atributo|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
