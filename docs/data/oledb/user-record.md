---
title: Registro de usuario
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: d6920a73f107f226cc31cb27fd15178f6d2f1c26
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525264"
---
# <a name="user-record"></a>Registro de usuario

> [!NOTE] 
> El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

El registro de usuario proporciona la estructura de código y los datos que representan la columna de datos de un conjunto de filas. Puede crearse un registro de usuario en tiempo de compilación o de ejecución. Cuando se crea un proveedor mediante el **Asistente para proveedores OLE DB ATL**, este crea un registro de usuario predeterminado que tiene este aspecto (suponiendo que ha especificado un nombre de proveedor [nombre corto] de *miProveedor*):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

Las plantillas de proveedor OLE DB controlen todos los detalles de OLE DB en las interacciones con el cliente. Para adquirir los datos de columna necesarios para una respuesta, el proveedor llama a la función `GetColumnInfo`, que se debe colocar en el registro de usuario. Puede invalidar explícitamente `GetColumnInfo` en el registro de usuario, por ejemplo, por declararlo en el archivo .h como se muestra aquí:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

Esto equivale a lo siguiente:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

A continuación, implemente `GetColumnInfo` en el archivo .cpp del registro de usuario.

Las macros PROVIDER_COLUMN_MAP ayudan a crear una función `GetColumnInfo`:

- BEGIN_PROVIDER_COLUMN_MAP define el prototipo de función y una matriz estática de estructuras `ATLCOLUMNINFO`.

- PROVIDER_COLUMN_ENTRY define e inicializa una sola instancia de `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP cierra la matriz y la función. También coloca el número de elementos de matriz en el parámetro *pcCols*.

Cuando se crea un registro de usuario en tiempo de ejecución, `GetColumnInfo` usa el parámetro *pThis* para recibir un puntero a una instancia de conjunto de filas o comando. Los comandos y conjuntos de filas deben admitir la interfaz `IColumnsInfo`, por lo que se puede obtener la información de la columna de este puntero.

`CommandClass` y `RowsetClass` son el comando y el conjunto de filas que utiliza el registro de usuario.

Para obtener un ejemplo más detallado de cómo invalidar `GetColumnInfo` en un registro de usuario, consulte [Determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
