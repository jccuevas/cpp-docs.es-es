---
title: 'CDynamicParameterAccessor:: Setparamstring | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs: C++
helpviewer_keywords: SetParamString method
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff96f451bc60469df0469d6a002ec51d91743b89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparamstring"></a>CDynamicParameterAccessor::SetParamString
Establece los datos de cadena del parámetro especificado almacenado en el búfer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nParam`  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro basándose en su orden en el SQL o una llamada al procedimiento almacenado. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pString`  
 [in] Un puntero a ANSI (**CHAR**) o Unicode (**WCHAR**) los datos del parámetro especificado de cadena. Vea `DBSTATUS` en oledb.h.  
  
 *status*  
 [in] El `DBSTATUS` estado del parámetro especificado. Para obtener información sobre `DBSTATUS` valores, consulte [estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en el *referencia del programador de OLE DB*, o busque `DBSTATUS` en oledb.h.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
 `SetParamString`se producirá un error si intenta establecer una cadena que es mayor que el tamaño máximo especificado para `pString`.  
  
 Use `SetParamString` para establecer los datos de parámetro de cadena en el búfer. Use [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para establecer los datos de parámetro que no sean en el búfer.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)