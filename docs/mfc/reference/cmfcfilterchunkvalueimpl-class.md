---
title: "CMFCFilterChunkValueImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFilterChunkValueImpl"
  - "afxwin/CMFCFilterChunkValueImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFilterChunkValueImpl class"
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCFilterChunkValueImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ésta es una clase que simplifica la pieza y la lógica de los pares de valores de propiedad.  
  
## Sintaxis  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl.md)|Destructs el objeto.|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl.md)|construye el objeto.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](../Topic/CMFCFilterChunkValueImpl::Clear.md)|borra el ChunkValue.|  
|[CMFCFilterChunkValueImpl::CopyChunk](../Topic/CMFCFilterChunkValueImpl::CopyChunk.md)|Copia este fragmento a una estructura que describe las características de un fragmento.|  
|[CMFCFilterChunkValueImpl::CopyFrom](../Topic/CMFCFilterChunkValueImpl::CopyFrom.md)|Inicializa este valor de piezas de otro valor.|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](../Topic/CMFCFilterChunkValueImpl::GetChunkGUID.md)|Recupera el fragmento GUID.|  
|[CMFCFilterChunkValueImpl::GetChunkPID](../Topic/CMFCFilterChunkValueImpl::GetChunkPID.md)|Recupera el fragmento PID \(id. de la propiedad\).|  
|[CMFCFilterChunkValueImpl::GetChunkType](../Topic/CMFCFilterChunkValueImpl::GetChunkType.md)|Obtiene el tipo de fragmento.|  
|[CMFCFilterChunkValueImpl::GetString](../Topic/CMFCFilterChunkValueImpl::GetString.md)|Recupera el valor de cadena.|  
|[CMFCFilterChunkValueImpl::GetValue](../Topic/CMFCFilterChunkValueImpl::GetValue.md)|Recupera el valor como propvariant asignada.|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](../Topic/CMFCFilterChunkValueImpl::GetValueNoAlloc.md)|Valor no asignado especificado \(el valor interno\).|  
|[CMFCFilterChunkValueImpl::IsValid](../Topic/CMFCFilterChunkValueImpl::IsValid.md)|Comprueba si el valor de propiedad es válido o no.|  
|[CMFCFilterChunkValueImpl::SetBoolValue](../Topic/CMFCFilterChunkValueImpl::SetBoolValue.md)|Sobrecargado.  Establece la propiedad por la clave a un booleano.|  
|[CMFCFilterChunkValueImpl::SetDwordValue](../Topic/CMFCFilterChunkValueImpl::SetDwordValue.md)|Establece la propiedad por clave a DWORD.|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](../Topic/CMFCFilterChunkValueImpl::SetFileTimeValue.md)|Establece la propiedad por la clave a un filetime.|  
|[CMFCFilterChunkValueImpl::SetInt64Value](../Topic/CMFCFilterChunkValueImpl::SetInt64Value.md)|Establece la propiedad por la clave a un int64.|  
|[CMFCFilterChunkValueImpl::SetIntValue](../Topic/CMFCFilterChunkValueImpl::SetIntValue.md)|Establece la propiedad por clave en int.|  
|[CMFCFilterChunkValueImpl::SetLongValue](../Topic/CMFCFilterChunkValueImpl::SetLongValue.md)|Establece la propiedad por la clave a un LONG.|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](../Topic/CMFCFilterChunkValueImpl::SetSystemTimeValue.md)|Establece la propiedad por la clave a un SystemTime.|  
|[CMFCFilterChunkValueImpl::SetTextValue](../Topic/CMFCFilterChunkValueImpl::SetTextValue.md)|Establece la propiedad por clave a una cadena Unicode.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](../Topic/CMFCFilterChunkValueImpl::SetChunk.md)|Una función auxiliar que establece las propiedades comunes del fragmento.|  
  
## Comentarios  
 Para utilizar, crea simplemente una clase de CMFCFilterChunkValueImpl de la clase de la derecha  
  
 Ejemplo:  
  
 Fragmento de CMFCFilterChunkValueImpl;  
  
 hora \= chunk.SetBoolValue \(PKEY\_IsAttachment, true\);  
  
 o  
  
 hora \= chunk.SetFileTimeValue \(PKEY\_ItemDate, ftLastModified\);  
  
## Jerarquía de herencia  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)