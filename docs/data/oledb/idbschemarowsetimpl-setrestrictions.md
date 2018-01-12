---
title: 'IDBSchemaRowsetImpl:: SetRestrictions | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
dev_langs: C++
helpviewer_keywords: SetRestrictions method
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23d4932508d8abeb96dad1dd0f70e396c7240168
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimplsetrestrictions"></a>IDBSchemaRowsetImpl::SetRestrictions
Especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void SetRestrictions(  
   ULONG cRestrictions,  
   GUID* /* rguidSchema */,  
   ULONG* rgRestrictions   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cRestrictions`  
 [in] El número de restricciones en la matriz de `rgRestrictions` y el número de GUID en la matriz de `rguidSchema` .  
  
 `rguidSchema`  
 [in] Una matriz de GUID de conjuntos de filas de esquema para los que se deben obtener restricciones. Cada elemento de la matriz contiene el GUID de un conjunto de filas de esquema (por ejemplo, `DBSCHEMA_TABLES`).  
  
 `rgRestrictions`  
 [in] Una matriz de longitud `cRestrictions` de los valores de restricción que se establezcan. Cada elemento corresponde a las restricciones en el conjunto de filas de esquema identificado por el GUID. Si el proveedor no admite un conjunto de filas de esquema, el elemento se establece en cero. De otro modo, el valor de **ULONG** contiene una máscara de bits que representa las restricciones admitidas en ese conjunto de filas de esquema. Para obtener más información sobre qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla del conjunto de filas de esquema GUID en [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el *referencia del programador de OLE DB* en las ventanas SDK.  
  
## <a name="remarks"></a>Comentarios  
 El objeto de **IDBSchemaRowset** llama a `SetRestrictions` para determinar qué restricciones se admiten en un conjunto de filas de esquema determinado ( [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) llama mediante un puntero de conversión hacia arriba). Las restricciones permiten a los clientes obtener solo las filas coincidentes (por ejemplo, buscar todas las columnas de la tabla "MyTable"). Las restricciones son opcionales y, en caso de que no se admita ninguna (comportamiento predeterminado), se devuelven siempre todos los datos.  
  
 La implementación predeterminada de este método establece los elementos de la matriz `rgRestrictions` en 0. Reemplace el valor predeterminado en la clase de sesión para establecer restricciones distintas de las predeterminadas.  
  
 Para obtener información sobre cómo implementar la compatibilidad de conjunto de filas de esquema, vea [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).  
  
 Para obtener un ejemplo de un proveedor que admite conjuntos de filas de esquema, vea el ejemplo [UpdatePV](../../visual-cpp-samples.md) .  
  
 Para obtener más información sobre conjuntos de filas de esquema, consulte [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el *referencia del programador de OLE DB* del SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (clase)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../visual-cpp-samples.md)