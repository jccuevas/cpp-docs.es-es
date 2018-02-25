---
title: ICommandTextImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c74ad1da299c05ade422596b08d48f33f9d22e37
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl (Clase)
Proporciona una implementación para el [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Deriva de la clase de comando **ICommandTextImpl**.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|Establece el texto del comando, reemplazando el texto del comando existente.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|Almacena el texto del comando.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria acerca de los comandos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** altdb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)