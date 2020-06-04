---
title: Agregar una interfaz a un proveedor
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: b13d1224388dc7d3218dea1c70b5aa8a595fcbdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212336"
---
# <a name="adding-an-interface-to-your-provider"></a>Agregar una interfaz a un proveedor

> [!NOTE]
> El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

Determine el objeto que desea agregar a la interfaz (normalmente, el origen de los datos, el conjunto de filas, el comando o los objetos de sesión creados por el **Asistente para proveedores OLE DB**). Es posible que el objeto que deba agregar a la interfaz es que el proveedor no admite actualmente. En ese caso, ejecute el **Asistente para proveedores OLE DB ATL** para crear el objeto. Haga clic con el botón derecho en el proyecto en **Vista de clases**, haga clic en **Agregar** > **Nuevo elemento** en el menú, seleccione **Instalado** > **Visual C++**  > **ATL** y, a continuación, haga clic en **Proveedor OLEDB ATL**. Le recomendamos colocar el código de interfaz en un directorio independiente y, a continuación, copiar los archivos en el proyecto de proveedor.

Si ha creado una nueva clase para admitir la interfaz, haga que el objeto herede de esa clase. Por ejemplo, podría agregar la clase `IRowsetIndexImpl` a un objeto de conjunto de filas:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Agregue la interfaz a COM_MAP del objeto mediante la macro COM_INTERFACE_ENTRY. Si no hay ninguna asignación, cree uno. Por ejemplo:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Para el objeto de conjunto de filas, encadene la asignación de su elemento primario para que el objeto puede delegar a la clase primaria. En este ejemplo, agregue la macro COM_INTERFACE_ENTRY_CHAIN a la asignación:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
