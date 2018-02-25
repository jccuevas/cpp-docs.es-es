---
title: CRowsetImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0d97eefdc1885c532df9c9be913e3f1beea2ff09
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetimpl-class"></a>CRowsetImpl (Clase)
Proporciona una implementación de conjunto de filas de OLE DB estándar sin necesidad de herencia múltiple de las interfaces de implementación.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl <T, IRowset>   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Clase de usuario que se deriva de `CRowsetImpl`.  
  
 `Storage`  
 La clase de registro de usuario.  
  
 `CreatorClass`  
 La clase que contiene propiedades para el conjunto de filas; Normalmente el comando.  
  
 `ArrayType`  
 La clase que actuará como almacenamiento para los datos del conjunto de filas. Este parámetro tiene como valor predeterminado `CAtlArray`, pero puede ser cualquier clase que admita la funcionalidad necesaria.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|Extrae una cadena de un **DBID** y lo copia en el `bstr` pasado.|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|Valida y almacena el **DBID**s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Métodos reemplazables  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|Recupera información de columna para una solicitud de cliente en particular.|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|Comprueba si uno o ambos parámetros contienen valores de cadena y si es así, copia los valores de cadena a los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|Comprueba para ver si alguno o ambos **DBID**contienen valores de cadena y si es así, los copia a sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|De forma predeterminada, un `CAtlArray` que templatizes en el argumento de plantilla de registro de usuario para `CRowsetImpl`. Se puede utilizar otra clase de tipo de matriz cambiando el `ArrayType` argumento de plantilla `CRowsetImpl`.|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|Contiene comandos inicial del conjunto de filas.|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|Contiene el índice inicial del conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 `CRowsetImpl` Proporciona reemplazos realizados en el formulario de convierte estático. Los métodos controlan la manera en que un conjunto de filas determinado validará el texto del comando. Puede crear sus propias `CRowsetImpl`-clase de estilo mediante la realización de las interfaces de la implementación heredada de varios. El único método para el que debe proporcionar la implementación es **Execute**. Dependiendo de qué tipo de conjunto de filas se crea, los métodos de creador esperará firmas diferentes para **Execute**. Por ejemplo, si usas un `CRowsetImpl`-clase derivada para implementar un conjunto de filas de esquema, el **Execute** método tendrá la siguiente firma:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Si está creando un `CRowsetImpl`-clase derivada para implementar un comando o conjunto de filas de la sesión, el **Execute** método tendrá la siguiente firma:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 Para implementar cualquiera de los `CRowsetImpl`-derivado **Execute** métodos, debe rellenar los búferes de datos interna ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h