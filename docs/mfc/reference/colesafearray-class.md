---
title: "COleSafeArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], safe"
  - "COleSafeArray class"
  - "ODBC, safe arrays"
  - "safe arrays"
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleSafeArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase para trabajar con matrices del tipo y la dimensión arbitrarios.  
  
## Sintaxis  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleSafeArray::COleSafeArray](../Topic/COleSafeArray::COleSafeArray.md)|Crea un objeto `COleSafeArray`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleSafeArray::AccessData](../Topic/COleSafeArray::AccessData.md)|Recupera un puntero a los datos de la matriz.|  
|[COleSafeArray::AllocData](../Topic/COleSafeArray::AllocData.md)|Asigna memoria para la matriz.|  
|[COleSafeArray::AllocDescriptor](../Topic/COleSafeArray::AllocDescriptor.md)|Asigna memoria para la matriz segura descriptor.|  
|[COleSafeArray::Attach](../Topic/COleSafeArray::Attach.md)|Proporciona un control de matriz existente de **VARIANT** al objeto de `COleSafeArray` .|  
|[COleSafeArray::Clear](../Topic/COleSafeArray::Clear.md)|libera todos los datos en **VARIANT**subyacente.|  
|[COleSafeArray::Copy](../Topic/COleSafeArray::Copy.md)|Crea una copia de una matriz existente.|  
|[COleSafeArray::Create](../Topic/COleSafeArray::Create.md)|crea una matriz segura.|  
|[COleSafeArray::CreateOneDim](../Topic/COleSafeArray::CreateOneDim.md)|crea un objeto unidimensional de `COleSafeArray` .|  
|[COleSafeArray::Destroy](../Topic/COleSafeArray::Destroy.md)|Destruye una matriz existente.|  
|[COleSafeArray::DestroyData](../Topic/COleSafeArray::DestroyData.md)|destruye datos en una matriz segura.|  
|[COleSafeArray::DestroyDescriptor](../Topic/COleSafeArray::DestroyDescriptor.md)|destruye descriptor de una matriz segura.|  
|[COleSafeArray::Detach](../Topic/COleSafeArray::Detach.md)|Desasocia la matriz de **VARIANT** del objeto de `COleSafeArray` \(de modo que los datos no se liberan\).|  
|[COleSafeArray::GetByteArray](../Topic/COleSafeArray::GetByteArray.md)|Copia el contenido de la matriz segura en [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[COleSafeArray::GetDim](../Topic/COleSafeArray::GetDim.md)|Devuelve el número de dimensiones de la matriz.|  
|[COleSafeArray::GetElement](../Topic/COleSafeArray::GetElement.md)|Recupera un único elemento de la matriz segura.|  
|[COleSafeArray::GetElemSize](../Topic/COleSafeArray::GetElemSize.md)|Devuelve el tamaño, en bytes, de un elemento en una matriz segura.|  
|[COleSafeArray::GetLBound](../Topic/COleSafeArray::GetLBound.md)|Devuelve el límite inferior de cualquier dimensión de la matriz segura.|  
|[COleSafeArray::GetOneDimSize](../Topic/COleSafeArray::GetOneDimSize.md)|devuelve el número de elementos en el objeto unidimensional de `COleSafeArray` .|  
|[COleSafeArray::GetUBound](../Topic/COleSafeArray::GetUBound.md)|Devuelve el límite superior de cualquier dimensión de la matriz segura.|  
|[COleSafeArray::Lock](../Topic/COleSafeArray::Lock.md)|Incrementa el recuento de bloqueo de una matriz y coloca un puntero a los datos de la matriz en el descriptor de matriz.|  
|[COleSafeArray::PtrOfIndex](../Topic/COleSafeArray::PtrOfIndex.md)|Devuelve un puntero al elemento indizado.|  
|[COleSafeArray::PutElement](../Topic/COleSafeArray::PutElement.md)|Asigna un elemento de la matriz.|  
|[COleSafeArray::Redim](../Topic/COleSafeArray::Redim.md)|Cambia el mínima significativo \(de derecha\) enlazado de la matriz segura.|  
|[COleSafeArray::ResizeOneDim](../Topic/COleSafeArray::ResizeOneDim.md)|cambia el número de elementos en un objeto unidimensional de `COleSafeArray` .|  
|[COleSafeArray::UnaccessData](../Topic/COleSafeArray::UnaccessData.md)|Disminuye el recuento de bloqueo de una matriz y reemplaza el puntero recuperado por `AccessData`.|  
|[COleSafeArray::Unlock](../Topic/COleSafeArray::Unlock.md)|Disminuye el recuento de bloqueo de una matriz para que pueda liberar o cambiar de tamaño.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](../Topic/COleSafeArray::operator%20LPCVARIANT.md)|Tiene acceso a la estructura subyacente de **VARIANT** del objeto de `COleSafeArray` .|  
|[COleSafeArray::operator LPVARIANT](../Topic/COleSafeArray::operator%20LPVARIANT.md)|Tiene acceso a la estructura subyacente de **VARIANT** del objeto de `COleSafeArray` .|  
|[COleSafeArray::operator \=](../Topic/COleSafeArray::operator%20=.md)|Copia los valores de un objeto de `COleSafeArray` \(**SAFEARRAY**, **VARIANT**, `COleVariant`, o matriz de `COleSafeArray` \).|  
|[COleSafeArray::operator \=\=](../Topic/COleSafeArray::operator%20==.md)|compara dos matrices variables \(**SAFEARRAY**, **VARIANT**, `COleVariant`, o matrices de `COleSafeArray` \).|  
|[COleSafeArray::operator \<\<](../Topic/COleSafeArray::operator%20%3C%3C.md)|Representa el contenido de un objeto de `COleSafeArray` al contexto de volcado de memoria.|  
  
## Comentarios  
 `COleSafeArray` deriva de estructura OLE de **VARIANT** .  Las funciones miembro de OLE **SAFEARRAY** están disponibles a través de `COleSafeArray`, además de un conjunto de funciones miembro diseñadas específicamente para las matrices unidimensionales de bytes.  
  
## Jerarquía de herencia  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)