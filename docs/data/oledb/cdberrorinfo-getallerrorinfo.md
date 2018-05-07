---
title: 'Cdberrorinfo:: Getallerrorinfo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 590215ddc5c62e5c717aebe196bc33ce7d514e7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
Devuelve todos los tipos de información de error contenida en un registro de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```
HRESULT GetAllErrorInfo(ULONG ulRecordNum,  
   LCID lcid,  BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ulRecordNum*  
 [in] Número de base cero del registro para el que se va a devolver información de error.  
  
 `lcid`  
 [in] El identificador de configuración regional de la información de error va a devolver.  
  
 `pbstrDescription`  
 [out] Un puntero a una descripción de texto del error o NULL si no se admite la configuración regional. Vea la sección Comentarios.  
  
 `pbstrSource`  
 [out] Un puntero a una cadena que contiene el nombre del componente que generó el error.  
  
 `pguid`  
 [out] Un puntero al GUID de la interfaz que definió el error.  
  
 *pdwHelpContext*  
 [out] Un puntero al identificador del contexto de ayuda para el error.  
  
 *pbstrHelpFile*  
 [out] Un puntero a una cadena que contiene la ruta de acceso al archivo de ayuda que describe el error.  
  
## <a name="return-value"></a>Valor devuelto  
 `S_OK` si se realiza correctamente. Vea [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) en el *referencia del programador de OLE DB* para los demás valores devueltos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="remarks"></a>Comentarios  
 El valor de salida de `pbstrDescription` se obtienen internamente IErrorInfo:: GetDescription que realiza la llamada, que establece el valor en NULL si no se admite la configuración regional, o si se cumplen las condiciones siguientes:  
  
1.  el valor de `lcid` no es EE. UU. Inglés y  
  
2.  el valor de `lcid` es no igual que el valor devuelto por GetUserDefaultLCID.  
  
## <a name="see-also"></a>Vea también  
 [CDBErrorInfo (Clase)](../../data/oledb/cdberrorinfo-class.md)