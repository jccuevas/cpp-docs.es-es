---
title: 'CDataSource:: Getinitializationstring | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
dev_langs: C++
helpviewer_keywords: GetInitializationString method
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0cc70e9cb1c775cf9c19f7269a5305624d27210b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdatasourcegetinitializationstring"></a>CDataSource::GetInitializationString
Recupera la cadena de inicialización de un origen de datos que está abierto actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT GetInitializationString(   
   BSTR* pInitializationString,   
   bool bIncludePassword = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pInitializationString*  
 [out] Un puntero a la cadena de inicialización.  
  
 *bIncludePassword*  
 [in] **true** si la cadena incluye una contraseña; en caso contrario, **false**.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 La cadena de inicialización resultante puede utilizarse para después volver a abrir esta conexión de origen de datos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataSource (Clase)](../../data/oledb/cdatasource-class.md)