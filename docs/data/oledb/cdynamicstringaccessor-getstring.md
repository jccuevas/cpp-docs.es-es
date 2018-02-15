---
title: CDynamicStringAccessor::GetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c3ccef4046928be7ce62c845c99538f894bd1b3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
Recupera los datos de la columna especificada como una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Recupera un puntero al valor de cadena de la columna especificada. El valor es de tipo ***BaseType***, que será **CHAR** o **WCHAR** dependiendo de si se ha definido _UNICODE o no. Devuelve NULL si no se encuentra la columna especificada.  
  
## <a name="remarks"></a>Comentarios  
 El segundo invalidar formulario toma el nombre de columna como una cadena ANSI. La tercera invalidar formulario toma el nombre de columna como una cadena Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)