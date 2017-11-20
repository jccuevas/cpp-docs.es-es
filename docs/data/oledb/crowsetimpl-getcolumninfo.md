---
title: 'CRowsetImpl:: GetColumnInfo | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs: C++
helpviewer_keywords: GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1229a9f45d7bd0f4a2f80b8443179640cd9f8926
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
Recupera información de columna para una solicitud de cliente en particular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(  
   T* pv,  
   ULONG* pcCols   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] Un puntero para el usuario `CRowsetImpl` clase derivada.  
  
 `pcCols`  
 [in] Un puntero (de salida) para el número de columnas que se devuelven.  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero a una variable static **ATLCOLUMNINFO** estructura.  
  
## <a name="remarks"></a>Comentarios  
 Este método es un reemplazo avanzado.  
  
 Se llama a este método varias clases de implementación base para recuperar la información de columna para una solicitud de cliente en particular. Por lo general, debería llamar a este método `IColumnsInfoImpl`. Si invalida este método, debe colocar una versión del método en su `CRowsetImpl`-clase derivada. Dado que el método se puede colocar en una clase no es de plantilla, se debe cambiar `pv` correspondientes `CRowsetImpl`-clase derivada.  
  
 En el ejemplo siguiente se muestra **del GetColumnInfo** uso. En este ejemplo, **CMyRowset** es un `CRowsetImpl`-clase derivada. Para invalidar `GetColumnInfo` para todas las instancias de esta clase, coloque el siguiente método en el **CMyRowset** definición de clase:  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CRowsetImpl (Clase)](../../data/oledb/crowsetimpl-class.md)