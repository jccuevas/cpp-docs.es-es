---
title: espacio de nombres predeterminado | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f4386d3636744a673a10dd9530fd3836fdb78e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086956"
---
# <a name="default-namespace"></a>espacio de nombres predeterminado
El `default` establece el ámbito de espacio de nombres de los tipos integrados que son compatibles con C++ / CX.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace default;  
```  
  
### <a name="members"></a>Miembros  
 Todos los tipos integrados heredan los miembros siguientes.  
  
|||  
|-|-|  
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Determina si el objeto especificado es igual al objeto actual.|  
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Devuelve el código hash de esta instancia.|  
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Devuelve una cadena que representa el tipo actual.|  
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Devuelve una cadena que representa el tipo actual.|  
  
### <a name="built-in-types"></a>Tipos integrados  
  
|nombre|Descripción|  
|----------|-----------------|  
|`char16`|Un valor no numérico de 16 bits que representa un punto de código Unicode (UTF-16).|  
|`float32`|Número de punto flotante de 32 bits conforme a IEEE 754.|  
|`float64`|Número de punto flotante de 64 bits conforme a IEEE 754.|  
|`int16`|Entero de 16 bits con signo.|  
|`int32`|Entero de 32 bits con signo.|  
|`int64`|Entero de 64 bits con signo.|  
|`int8`|Valor numérico con signo de 8 bits.|  
|`uint16`|Entero de 16 bits sin signo.|  
|`uint32`|Entero de 32 bits sin signo.|  
|`uint64`|Entero de 64 bits sin signo.|  
|`uint8`|Valor numérico sin signo de 8 bits.|  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** vccorlib.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)