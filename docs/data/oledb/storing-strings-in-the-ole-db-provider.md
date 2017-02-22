---
title: "Almacenar cadenas en el proveedor OLE DB | Microsoft Docs"
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
  - "registros de usuario, editar"
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Almacenar cadenas en el proveedor OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En MyProviderRS.h, el Asistente para proveedores OLE DB ATL crea un registro de usuario predeterminado denominado `CWindowsFile`.  Para controlar las dos cadenas, modifique `CWindowsFile` o agregue su propio registro de usuario, de la forma indicada en el siguiente fragmento de código:  
  
```  
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 Los miembros de datos `szCommand` y `szText` representan las dos cadenas, y `szCommand2` y `szText2` proporcionan columnas adicionales si es necesario.  El miembro de datos `dwBookmark` no es necesario para el proveedor sencillo de sólo lectura, pero se utiliza posteriormente para agregar una interfaz `IRowsetLocate`; vea [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  El operador `==` compara instancias \(la implementación de este operador es opcional\).  
  
 Cuando se haga esto, el proveedor deberá estar preparado para compilar y ejecutar.  Para probar el proveedor, se necesita un consumidor con funcionalidad coincidente.  [Implementar un consumidor simple](../../data/oledb/implementing-a-simple-consumer.md) muestra la forma de crear un consumidor de prueba de este tipo.  Ejecute el consumidor de prueba con el proveedor.  Compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor cuando haga clic en el botón **Ejecutar** en el cuadro de diálogo **Consumidor de prueba**.  
  
 Cuando haya probado con éxito el proveedor, puede que desee ampliar su funcionalidad mediante la implementación de interfaces adicionales.  Se muestra un ejemplo en [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## Vea también  
 [Implementar un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)