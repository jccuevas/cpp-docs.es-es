---
title: 'CCommand:: Close | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 10d3ce633add0dea4a3b9a79a32fd380761b5a2f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandclose"></a>CCommand::Close
Libera el conjunto de filas de descriptor de acceso asociado con el comando.  
  
## <a name="syntax"></a>Sintaxis

```cpp
void Close();  
```  
  
## <a name="remarks"></a>Comentarios  
 Un comando usa un conjunto de filas, descriptor de acceso de conjunto de resultados y (opcionalmente) un descriptor de acceso de parámetro (a diferencia de las tablas, que no admiten parámetros y no es necesario un descriptor de acceso de parámetro).  
  
 Cuando se ejecuta un comando, debe llamar a ambos `Close` y [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) después del comando.  
  
 Si desea ejecutar el mismo comando de forma repetida, debe liberar cada descriptor de acceso del conjunto de resultados mediante una llamada a `Close` antes de llamar a `Execute`. Al final de la serie, debe liberar el descriptor de acceso de parámetro mediante una llamada a `ReleaseCommand`. Otro escenario común es llamar a un procedimiento almacenado con parámetros de salida. En muchos proveedores (por ejemplo, el proveedor OLE DB para SQL Server) los valores de parámetro de salida no será accesibles hasta que se cierre el descriptor de acceso del conjunto de resultados. Llame a `Close` para cerrar el conjunto de filas devuelto y el descriptor de acceso de conjunto de resultados, pero no el descriptor de acceso de parámetro, lo que le permite recuperar los valores de parámetro de salida.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se puede llamar a `Close` y `ReleaseCommand` cuando se ejecuta el mismo comando varias veces.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (clase)](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)