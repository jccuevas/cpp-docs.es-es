---
title: "CSettingsStore Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSettingsStore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStore class"
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CSettingsStore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La API de Windows ajustes funciona, proporcionando una interfaz orientado a objetos que se utiliza para obtener acceso al registro.  
  
## Sintaxis  
  
```  
class CSettingsStore : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStore::CSettingsStore](../Topic/CSettingsStore::CSettingsStore.md)|Crea un objeto `CSettingsStore`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStore::Close](../Topic/CSettingsStore::Close.md)|Cierra la clave del Registro abierto.|  
|[CSettingsStore::CreateKey](../Topic/CSettingsStore::CreateKey.md)|Abra la clave especificada o lo crea si no existe.|  
|[CSettingsStore::DeleteKey](../Topic/CSettingsStore::DeleteKey.md)|Elimina la clave especificada y todos sus elementos secundarios.|  
|[CSettingsStore::DeleteValue](../Topic/CSettingsStore::DeleteValue.md)|Elimina el valor especificado de la tecla abrir.|  
|[CSettingsStore::Open](../Topic/CSettingsStore::Open.md)|Abra la clave especificada.|  
|[CSettingsStore::Read](../Topic/CSettingsStore::Read.md)|Recupera los datos por un valor de clave especificado.|  
|[CSettingsStore::Write](../Topic/CSettingsStore::Write.md)|Escribe un valor en el registro bajo la clave abierto.|  
  
## Comentarios  
 Las funciones `CreateKey` y `Open` miembro son muy similares.  Si existe la clave del Registro ya, `CreateKey` y función de `Open` de la misma manera.  Sin embargo, si no existe la clave del Registro, `CreateKey` lo creará mientras `Open` devolverá un valor de error.  
  
## Ejemplo  
 El siguiente ejemplo se muestra cómo utilizar el Abrir y leer los métodos de `CSettingsStore` ordenar.  Este fragmento de código es parte de [Ejemplo de demostración de información sobre herramientas](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/CPP/csettingsstore-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSettingsStore](../../mfc/reference/csettingsstore-class.md)  
  
## Requisitos  
 **encabezado:** afxsettingsstore.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)