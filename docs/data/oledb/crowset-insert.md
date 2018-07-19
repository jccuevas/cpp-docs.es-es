---
title: 'CRowset:: Insert | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs:
- C++
helpviewer_keywords:
- Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44dddd6f3da835744463a9a95c44aa224d29d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098451"
---
# <a name="crowsetinsert"></a>CRowset::Insert
Crea e inicializa una nueva fila con datos del descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Insert(int nAccessor = 0,   
   bool bGetHRow = false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nAccessor`  
 [in] El número del descriptor de acceso que se utilizará para insertar los datos.  
  
 *bGetHRow*  
 [in] Indica si se recupera el identificador de la fila insertada.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional `IRowsetChange`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetChange** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 INSERT puede producir un error si no se puede escribir una o varias columnas. Modifique la asignación del cursor para corregirlo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo tener acceso a un origen de datos a través de un conjunto de filas y, a continuación, insertar una cadena con una tabla en ese conjunto de filas.  
  
 En primer lugar, cree una clase de tabla mediante la inserción de un nuevo objeto ATL en el proyecto. Por ejemplo, haga clic en el proyecto en el panel de área de trabajo y seleccione **nuevo objeto ATL**. Desde el **acceso a datos** categoría, seleccione **consumidor**. Crear un objeto de consumidor de tipo **tabla**. (Seleccione **tabla** crea un conjunto de filas directamente de la tabla; seleccionar **comandos** crea un conjunto de filas a través de un comando SQL.) Seleccione un origen de datos, especificar una tabla a través de la que se va a obtener acceso a ese origen de datos. Si se llama a su objeto de consumidor **CCustomerTable**, a continuación, podría implementar el código de inserción como sigue:  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (Clase)](../../data/oledb/crowset-class.md)