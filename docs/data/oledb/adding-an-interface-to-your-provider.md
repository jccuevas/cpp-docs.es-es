---
title: Agregar una interfaz a un proveedor
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 295a7955b78918d6281a28b616f201869f37b01e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488678"
---
# <a name="adding-an-interface-to-your-provider"></a>Agregar una interfaz a un proveedor

Determinar qué objeto que desea agregar la interfaz a (normalmente datos origen, conjunto de filas, comando o sesión de los objetos creados por el Asistente para proveedores OLE DB). Es posible que el objeto que deba agregar a la interfaz es que el proveedor no admite actualmente. En ese caso, ejecute el Asistente para proveedores OLE DB ATL para crear el objeto. Haga clic en el proyecto en la vista de clases, haga clic en **Agregar clase** desde el **agregar** menú y, a continuación, haga clic en **proveedor OLE DB ATL**. Es posible que desee colocar el código de interfaz en un directorio independiente y, a continuación, copie los archivos en el proyecto de proveedor.

Si ha creado una nueva clase para admitir la interfaz, que el objeto que se hereden de esa clase. Por ejemplo, podría agregar la clase **IRowsetIndexImpl** a un objeto de conjunto de filas:

```cpp
template <class Creator>
class CAgentRowset :
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,
    public IRowsetIndexImpl< ... >
```

Agregar a la interfaz **COM_MAP** en el objeto mediante la macro COM_INTERFACE_ENTRY. Si no hay ninguna asignación, cree uno. Por ejemplo:

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Para el objeto de conjunto de filas, la asignación de su elemento primario de la cadena de objetos para que el objeto puede delegar a la clase primaria. En este ejemplo, agregue la macro COM_INTERFACE_ENTRY_CHAIN al mapa:

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)