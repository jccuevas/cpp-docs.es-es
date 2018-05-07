---
title: Namespace Metadata | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
dev_langs:
- C++
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11dc54463207efade9a8ebb7179654d0b1e18909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata (Espacio de nombres)
Este espacio de nombres contiene atributos que modifican las declaraciones de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
  
namespace Platform {  
   namespace Metadata {  
}}  
```  
  
### <a name="members"></a>Miembros  
 Aunque este espacio de nombres está previsto para uso interno, los exploradores pueden mostrar los siguientes miembros de este espacio de nombres.  
  
|nombre|Observación|  
|----------|------------|  
|Atributo|La clase base de los atributos.|  
|[Platform::Metadata::DefaultMemberAttribute (Atributo)](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Indica la función preferida que se va a invocar entre varias funciones sobrecargadas posibles.|  
|[Atributo Platform::Metadata::FlagsAttribute](../cppcx/platform-metadata-flagsattribute-attribute.md)Flags|Declara una enumeración como enumeración de campos de bits.<br /><br /> En el siguiente ejemplo se muestra cómo aplicar el atributo `Flags` a una enumeración.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|  
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Garantiza que una clase ref privada tiene un nombre de clase en tiempo de ejecución válido.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Platform`  
  
### <a name="requirements"></a>Requisitos  
 **Metadatos:** platform.winmd  
  
 **Espacio de nombres:** Platform::Metadata  
  
## <a name="see-also"></a>Vea también  
 [Namespace de plataforma](platform-namespace-c-cx.md)