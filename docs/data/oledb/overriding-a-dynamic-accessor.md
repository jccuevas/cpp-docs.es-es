---
title: Invalidar un descriptor de acceso dinámico | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
- overriding, dynamic accessors
ms.assetid: cbefd156-6da5-490d-b795-c2d7d874f7ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8e76aefefd4a8b1ab41d084c1e02d0c38ab5c498
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990001"
---
# <a name="overriding-a-dynamic-accessor"></a>Invalidar un descriptor de acceso dinámico

Cuando se usa un descriptor de acceso dinámico, como `CDynamicAccessor`, el comando `Open` método crea un descriptor de acceso automáticamente, según la información de columna del conjunto de filas abierto. Puede reemplazar el descriptor de acceso dinámico para controlar exactamente cómo se enlazan las columnas.  
  
Para reemplazar el descriptor de acceso dinámico, pase **false** como el último parámetro para el `CCommand::Open` método. Esto evita que `Open` pueda crear automáticamente un descriptor de acceso. A continuación, puede llamar a `GetColumnInfo` y llamar a `AddBindEntry` para cada columna que desea enlazar. El código siguiente muestra cómo hacerlo:  
  
```cpp  
USES_CONVERSION;  
double   dblProductID;  
  
CCommand<CDynamicAccessor> product;  
// Open the table, passing false to prevent automatic binding   
product.Open(session, _T("Select * FROM Products"), NULL, NULL, DBGUID_DEFAULT, false);  
  

ULONG         nColumns;  
DBCOLUMNINFO*   pColumnInfo;  
// Get the column information from the opened rowset.  
product.GetColumnInfo(&nColumns, &pColumnInfo);  
  
// Bind the product ID as a double.  
pColumnInfo[0].wType          = DBTYPE_R8;  
pColumnInfo[0].ulColumnSize = 8;  
product.AddBindEntry(pColumnInfo[0]);  
  
// Bind the product name as it is.  
product.AddBindEntry(pColumnInfo[1]);  
  
// Bind the reorder level as a string.  
pColumnInfo[8].wType          = DBTYPE_STR;  
pColumnInfo[8].ulColumnSize = 10;  
product.AddBindEntry(pColumnInfo[8]);  
  
// You have finished specifying the bindings. Go ahead and bind.  
product.Bind();  
// Free the memory for the column information that was retrieved in   
// previous call to GetColumnInfo.  
CoTaskMemFree(pColumnInfo);  
  

char*   pszProductName;  
char*   pszReorderLevel;  
bool   bRC;  
  
// Loop through the records tracing out the information.  
while (product.MoveNext() == S_OK)  
{  
   bRC = product.GetValue(1, &dblProductID);  
   pszProductName   = (char*)product.GetValue(2);  
   pszReorderLevel  = (char*)product.GetValue(9);  
  
   ATLTRACE(_T("Override = %lf \"%s\" \"%s\"\n"), dblProductID,  
      A2T(pszProductName), A2T(pszReorderLevel));  
}  
```  
  
## <a name="see-also"></a>Vea también  

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)