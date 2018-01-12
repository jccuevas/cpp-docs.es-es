---
title: 'CDynamicStringAccessor:: SetString | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs: C++
helpviewer_keywords: SetString method
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c05186d8ea7f62ad07cae9a4b4689083543e485
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicstringaccessorsetstring"></a>CDynamicStringAccessor::SetString
Establece los datos de la columna especificada como una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. El valor especial 0 hace referencia a la columna de marcador, si lo hay.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `data`  
 [in] Un puntero a los datos de cadena se escriban en la columna especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero al valor de cadena que se va a establecer la columna especificada. El valor es de tipo `BaseType`, que será `CHAR` o `WCHAR` dependiendo de si `_UNICODE` está definido o no.  
  
## <a name="remarks"></a>Comentarios  
 El segundo invalidar formulario toma el nombre de columna como una cadena ANSI y la tercera invalidar formulario toma el nombre de columna como una cadena Unicode.  
  
 Si `_SECURE_ATL` se define con un valor distinto de cero, se generará un error de aserción en tiempo de ejecución si la entrada `data` cadena es mayor que la longitud máxima permitida de la columna de datos que se hace referencia. En caso contrario, la cadena de entrada se truncará si supera la longitud máxima permitida.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)