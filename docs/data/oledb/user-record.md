---
title: Registro de usuario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f8175694b10cc0c3c717a4fc5b5e02edca84ae60
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075086"
---
# <a name="user-record"></a>Registro de usuario

El registro de usuario proporciona la estructura de código y los datos que representa la columna de datos para un conjunto de filas. Puede crearse un registro de usuario en tiempo de compilación o en tiempo de ejecución. Cuando se crea un proveedor mediante el Asistente para proveedores OLE DB ATL, el asistente crea un registro de usuario predeterminado similar al siguiente (suponiendo que ha especificado un nombre de proveedor [short name] de "MyProvider"):  
  
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
  
Las plantillas de proveedor OLE DB controlen todos los detalles de OLE DB con respecto a las interacciones con el cliente. Para adquirir los datos de columna necesarios para una respuesta, el proveedor llama a la `GetColumnInfo` función, que se debe colocar en el registro de usuario. Puede invalidar explícitamente `GetColumnInfo` en el registro de usuario, por ejemplo, por declararlo en el archivo .h como se muestra aquí:  
  
```cpp  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
Esto equivale a:  
  
```cpp  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
También debe implementar `GetColumnInfo` en el archivo .cpp del registro de usuario.  
  
Las macros PROVIDER_COLUMN_MAP ayudan a crear un `GetColumnInfo` función:  
  
- BEGIN_PROVIDER_COLUMN_MAP define el prototipo de función y una matriz estática de `ATLCOLUMNINFO` estructuras.  
  
- PROVIDER_COLUMN_ENTRY define e inicializa una sola `ATLCOLUMNINFO`.  
  
- END_PROVIDER_COLUMN_MAP cierra la matriz y la función. También coloca el número de elementos de matriz en la *pcCols* parámetro.  
  
Cuando se crea un registro de usuario en tiempo de ejecución `GetColumnInfo` usa el *pThis* parámetro para recibir un puntero a una instancia de conjunto de filas o un comando. Los comandos y conjuntos de filas deben admitir la `IColumnsInfo` interfaz, por lo que puede obtenerse información de la columna de este puntero.  
  
`CommandClass` y `RowsetClass` son el comando y el conjunto de filas que se utiliza el registro de usuario.  
  
Para obtener un ejemplo más detallado de cómo invalidar `GetColumnInfo` en un registro de usuario, consulte [determinar dinámicamente las columnas se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Vea también  

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)