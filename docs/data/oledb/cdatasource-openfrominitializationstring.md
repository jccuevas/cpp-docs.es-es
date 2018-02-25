---
title: 'CDataSource:: OpenFromInitializationString | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs:
- C++
helpviewer_keywords:
- OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f05654c9b8647f62d967f97fa4b373471e049cda
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
Abre un origen de datos especificado por la cadena de inicialización proporcionada por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *szInitializationString*  
 [in] La cadena de inicialización.  
  
 *fPromptForInfo*  
 [in] Si este argumento se establece en **true**, a continuación, `OpenFromInitializationString` establecerá el **DBPROP_INIT_PROMPT** propiedad **DBPROMPT_COMPLETEREQUIRED**, que especifica que el usuario sea solicitando solo si se necesita más información. Esto es útil en situaciones en que la cadena de inicialización especifica una base de datos requiere una contraseña, pero la cadena no contiene la contraseña. El usuario se le pedirá una contraseña (o cualquier otra información que falte) al intentar conectarse a la base de datos.  
  
 El valor predeterminado es **false**, que especifica que el usuario nunca se le pida (establece **DBPROP_INIT_PROMPT** a **DBPROMPT_NOPROMPT**).  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataSource (Clase)](../../data/oledb/cdatasource-class.md)