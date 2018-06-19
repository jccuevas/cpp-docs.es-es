---
title: 'CUtlProps:: Oninterfacerequested | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50a1f17294a91446e71a51ffdac6c5aec83f2c9a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099776"
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
Administra las solicitudes de una interfaz opcional cuando un consumidor llama a un método en uno de los objetos interfaces de creación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 [in] El IID de la interfaz solicitada. Para obtener más información, vea la descripción de la `riid` parámetro de `ICommand::Execute` en el *referencia del programador de OLE DB* (en el *SDK de MDAC*).  
  
## <a name="remarks"></a>Comentarios  
 **OnInterfaceRequested** administra las solicitudes de consumidor de una interfaz opcional cuando un consumidor llama a un método en uno de los objetos interfaces de creación (como **IDBCreateSession**, **IDBCreateCommand**, `IOpenRowset`, o `ICommand`). Establece la propiedad de OLE DB correspondiente para la interfaz solicitada. Por ejemplo, si el consumidor solicita **IID_IRowsetLocate**, **OnInterfaceRequested** establece la **DBPROP_IRowsetLocate** interfaz. Si lo hace, mantiene el estado correcto durante la creación del conjunto de filas.  
  
 Se llama a este método cuando el consumidor llama **IOpenRowset:: OpenRowset** o `ICommand::Execute`.  
  
 Si un consumidor abre un objeto y solicita una interfaz opcional, el proveedor debe establecer la propiedad asociada con esa interfaz a `VARIANT_TRUE`. Debe permitir el procesamiento específico de la propiedad, **OnInterfaceRequested** se invoca antes que el proveedor **Execute** se llama al método. De forma predeterminada, **OnInterfaceRequested** controla las siguientes interfaces:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 Si desea controlar otras interfaces, invalidan esta función en la clase de origen, session, comando o conjunto de filas de datos a las funciones de proceso. La invalidación debe avanzar por las interfaces de propiedades get/set normal para asegurarse de que establecer las propiedades también establece las propiedades encadenadas (vea [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)