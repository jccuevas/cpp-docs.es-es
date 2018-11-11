---
title: Agregar una interfaz a un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 5659078641439744c1f68cbb399c19b9b58bd0bb
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265144"
---
# <a name="adding-an-interface-to-your-provider"></a>Agregar una interfaz a un proveedor

Determinar el objeto al que desea agregar a la interfaz (normalmente, los objetos de origen, conjunto de filas, comando o sesión de datos crean por el **Asistente para proveedores OLE DB**). Es posible que el objeto que deba agregar a la interfaz es que el proveedor no admite actualmente. En ese caso, ejecute el **el Asistente para proveedores OLE DB ATL** para crear el objeto. Haga clic en el proyecto en **vista de clases**, haga clic en **agregar** > **nuevo elemento** en el menú, seleccione **instalado**  >  **Visual C++** > **ATL**y, a continuación, haga clic en **proveedor OLEDB ATL**. Es posible que desee colocar el código de interfaz en un directorio independiente y, a continuación, copie los archivos en el proyecto de proveedor.

Si ha creado una nueva clase para admitir la interfaz, que el objeto que se hereden de esa clase. Por ejemplo, podría agregar la clase `IRowsetIndexImpl` a un objeto de conjunto de filas:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Agregar la interfaz a COM_MAP del objeto mediante la macro COM_INTERFACE_ENTRY. Si no hay ninguna asignación, cree uno. Por ejemplo:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Para el objeto de conjunto de filas, la asignación de su elemento primario de la cadena de objetos para que el objeto puede delegar a la clase primaria. En este ejemplo, agregue la macro COM_INTERFACE_ENTRY_CHAIN al mapa:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)