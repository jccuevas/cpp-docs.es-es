---
title: "CSettingsStoreSP Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSettingsStoreSP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStoreSP class"
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSettingsStoreSP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CSettingsStoreSP` es una clase auxiliar que puede utilizar para crear instancias de [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).  
  
## Sintaxis  
  
```  
class CSettingsStoreSP  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](../Topic/CSettingsStoreSP::CSettingsStoreSP.md)|Crea un objeto `CSettingsStoreSP`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](../Topic/CSettingsStoreSP::Create.md)|Crea una instancia de una clase que se deriva de `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](../Topic/CSettingsStoreSP::SetRuntimeClass.md)|Establece la clase en tiempo de ejecución.  El método de `Create` utiliza la clase en tiempo de ejecución para determinar qué clase de objetos a crear.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|`m_dwUserData`|Datos de usuario personalizado que se almacena en el objeto de `CSettingsStoreSP` .  Se proporciona estos datos en el constructor del objeto de `CSettingsStoreSP` .|  
|`m_pRegistry`|`CSettingsStore`\- objeto derivado que el método de `Create` crea.|  
  
## Comentarios  
 Puede utilizar la clase de `CSettingsStoreSP` para redirigir todas las operaciones del registro de MFC a otras ubicaciones, como un archivo XML o una base de datos.  Para ello, siga estos pasos:  
  
1.  Cree una clase \(como `CMyStore`\) y derívela de `CSettingsStore`.  
  
2.  Use las macros de [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) y de [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md) con la clase personalizada de `CSettingsStore` para habilitar la creación dinámica.  
  
3.  Reemplazar las funciones virtuales e implementar `Read` y `Write` funciona en la clase personalizada.  Implementar cualquier otra funcionalidad a los datos de lectura y escritura en la ubicación deseada.  
  
4.  En la aplicación, la llamada `CSettingsStoreSP::SetRuntimeClass` y pase un puntero a [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md) obtenido de la clase.  
  
 Siempre que el marco tuviera acceso normalmente al registro, ahora creará dinámicamente instancias de la clase personalizada y utilizarla para leer o escribir datos.  
  
 `CSettingsStoreSP::SetRuntimeClass` utiliza una variable estática global.  Por consiguiente, solo un almacén de custom está disponible al mismo tiempo.  
  
## Requisitos  
 **encabezado:** afxsettingsstore.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)