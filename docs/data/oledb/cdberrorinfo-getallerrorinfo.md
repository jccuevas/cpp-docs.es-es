---
title: "CDBErrorInfo::GetAllErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDBErrorInfo.GetAllErrorInfo"
  - "CDBErrorInfo::GetAllErrorInfo"
  - "ATL::CDBErrorInfo::GetAllErrorInfo"
  - "GetAllErrorInfo"
  - "CDBErrorInfo.GetAllErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAllErrorInfo (método)"
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetAllErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve todos los tipos de información de error incluidos en un registro de errores.  
  
## Sintaxis  
  
```  
  
      HRESULT GetAllErrorInfo(  
   ULONG ulRecordNum,  
   LCID lcid,  
   BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL  
) const throw( );  
```  
  
#### Parámetros  
 *ulRecordNum*  
 \[in\] El número cero\- basado en registro para que devuelva información de error.  
  
 `lcid`  
 \[in\] El identificador de configuración regional para que la información de error se devuelven.  
  
 `pbstrDescription`  
 \[out\] Un puntero a una descripción del texto de error o de NULL si la configuración regional no se admite.  Vea la sección Comentarios.  
  
 `pbstrSource`  
 \[out\] Un puntero a una cadena que contiene el nombre del componente que generó el error.  
  
 `pguid`  
 \[out\] Un puntero al GUID de la interfaz que definió el error.  
  
 *pdwHelpContext*  
 \[out\] Un puntero al Id. de contexto de ayuda para el error.  
  
 *pbstrHelpFile*  
 \[out\] Un puntero a una cadena que contiene la ruta de acceso al archivo de ayuda que describe el error.  
  
## Valor devuelto  
 `S_OK` si es correcto.  Vea [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) en *la referencia del* programador para otros valores devueltos.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Comentarios  
 El valor de salida de `pbstrDescription` se recopilan internamente llamando a IErrorInfo::GetDescription, que establece el valor en NULL si la configuración regional no se admite, o si se cumplen las dos condiciones siguientes:  
  
1.  el valor de `lcid` es inglés NOT US y.  
  
2.  el valor de `lcid` es NOT igual al valor devuelto por GetUserDefaultLCID.  
  
## Vea también  
 [CDBErrorInfo \(Clase\)](../../data/oledb/cdberrorinfo-class.md)