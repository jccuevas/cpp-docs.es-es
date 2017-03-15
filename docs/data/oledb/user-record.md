---
title: "Registro de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proveedores OLE DB, registro de usuario"
  - "registros, usuario"
  - "conjuntos de filas, registro de usuario"
  - "registros de usuario"
  - "registros de usuario, descripción"
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Registro de usuario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El registro de usuario proporciona el código y la estructura de datos que representa la columna de datos para un conjunto de filas.  Un registro de usuario puede crearse en tiempo de compilación o en tiempo de ejecución.  Cuando cree un proveedor mediante el Asistente para proveedores OLE DB ATL, el asistente crea un registro de usuario predeterminado con la siguiente apariencia \(suponiendo que especifica como nombre de proveedor \[nombre corto\] "MyProvider"\):  
  
```  
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
  
 Las plantillas de proveedor OLE DB controlan todos los detalles de OLE DB relativos a las interacciones con el cliente.  Para adquirir los datos de columna necesarios para una respuesta, el proveedor llama a la función `GetColumnInfo`, que se debe colocar en el registro de usuario.  Se puede reemplazar explícitamente `GetColumnInfo` en el registro de usuario, por ejemplo, declarándola en el archivo .h como se indica a continuación:  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 Esto equivale a:  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 También se debe implementar `GetColumnInfo` en el archivo .cpp del registro de usuario.  
  
 Las macros PROVIDER\_COLUMN\_MAP ayudan a crear una función `GetColumnInfo`:  
  
-   BEGIN\_PROVIDER\_COLUMN\_MAP define el prototipo de función y una matriz estática de estructuras **ATLCOLUMNINFO**.  
  
-   PROVIDER\_COLUMN\_ENTRY define e inicializa una única estructura **ATLCOLUMNINFO**.  
  
-   END\_PROVIDER\_COLUMN\_MAP cierra la matriz y la función.  También coloca el número de elementos de la matriz en el parámetro `pcCols`.  
  
 Cuando se crea un registro de usuario en tiempo de ejecución, **GetColumnInfo**  utiliza el parámetro `pThis` para recibir un puntero a una instancia de un conjunto de filas o de un comando.  Los comandos y conjuntos de filas deben ser compatibles con la interfaz `IColumnsInfo`, de forma que pueda obtenerse la información de columna con este puntero.  
  
 **CommandClass** y **RowsetClass** son el comando y el conjunto de filas que utilizan el registro de usuario.  
  
 Para consultar un ejemplo más detallado sobre cómo reemplazar `GetColumnInfo` en un registro de usuario, vea [Determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)