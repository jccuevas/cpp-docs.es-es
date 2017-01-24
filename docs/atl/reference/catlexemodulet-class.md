---
title: "CAtlExeModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlExeModuleT<T>"
  - "CAtlExeModuleT"
  - "ATL.CAtlExeModuleT<T>"
  - "ATL::CAtlExeModuleT"
  - "ATL.CAtlExeModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlExeModuleT class"
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlExeModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa el módulo para una aplicación.  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>  
class ATL_NO_VTABLE CAtlExeModuleT :  
   public CAtlModuleT< T >  
```  
  
#### Parámetros  
 `T`  
 la clase derivada de `CAtlExeModuleT`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlExeModuleT::CAtlExeModuleT](../Topic/CAtlExeModuleT::CAtlExeModuleT.md)|el constructor.|  
|[CAtlExeModuleT::~CAtlExeModuleT](../Topic/CAtlExeModuleT::~CAtlExeModuleT.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlExeModuleT::InitializeCom](../Topic/CAtlExeModuleT::InitializeCom.md)|Inicializa COM.|  
|[CAtlExeModuleT::ParseCommandLine](../Topic/CAtlExeModuleT::ParseCommandLine.md)|Analiza la línea de comandos y realiza el registro en caso necesario.|  
|[CAtlExeModuleT::PostMessageLoop](../Topic/CAtlExeModuleT::PostMessageLoop.md)|Se llama a este método inmediatamente después de salir del bucle de mensajes.|  
|[CAtlExeModuleT::PreMessageLoop](../Topic/CAtlExeModuleT::PreMessageLoop.md)|Este método se llama inmediatamente antes de escribir el bucle de mensajes.|  
|[CAtlExeModuleT::RegisterClassObjects](../Topic/CAtlExeModuleT::RegisterClassObjects.md)|Registra el objeto de clase.|  
|[CAtlExeModuleT::RevokeClassObjects](../Topic/CAtlExeModuleT::RevokeClassObjects.md)|Revoca el objeto de clase.|  
|[CAtlExeModuleT::Run](../Topic/CAtlExeModuleT::Run.md)|Este método ejecuta código en el módulo EXE para inicializar, ejecuta el bucle de mensajes, y limpia.|  
|[CAtlExeModuleT::RunMessageLoop](../Topic/CAtlExeModuleT::RunMessageLoop.md)|este método ejecuta el bucle de mensajes.|  
|[CAtlExeModuleT::UninitializeCom](../Topic/CAtlExeModuleT::UninitializeCom.md)|desinicializa COM.|  
|[CAtlExeModuleT::Unlock](../Topic/CAtlExeModuleT::Unlock.md)|Disminuye el recuento de bloqueo del módulo.|  
|[CAtlExeModuleT::WinMain](../Topic/CAtlExeModuleT::WinMain.md)|Este método implementa el código necesario ejecutar EXE.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlExeModuleT::m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md)|Un mensaje que indica que debe haber un retraso que cierra el módulo.|  
|[CAtlExeModuleT::m\_dwPause](../Topic/CAtlExeModuleT::m_dwPause.md)|Un valor de pausa utilizado para garantizar que todos los objetos se libera antes de cierre.|  
|[CAtlExeModuleT::m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md)|Un valor de tiempo de espera utilizado para retrasar descargar del módulo.|  
  
## Comentarios  
 `CAtlExeModuleT` representa el módulo para una aplicación \(EXE\) y contiene el código que permite crear un archivo EXE, procesar la línea de comandos, registrar objetos de clase, ejecutar el bucle de mensajes, y limpiar en la salida.  
  
 Esta clase está diseñado para mejorar el rendimiento cuando los objetos COM en el servidor EXE se crean y se destruyen continuamente.  Después de que se libere el objeto COM pasado, EXE espera una duración especificada por el miembro de datos de [CAtlExeModuleT:: m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md) .  Si no hay ninguna actividad durante este período \(es decir, no se crea ningún objeto COM\), se inicia el proceso de cierre.  
  
 El miembro de datos de [CAtlExeModuleT:: m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md) es un indicador utilizado para determinar si ÉSTE utiliza el mecanismo definido anteriormente.  Si se establece en false, el módulo finalizará inmediatamente.  
  
 Para obtener más información sobre los módulos de ATL, vea [Clases de módulo ATL](../../atl/atl-module-classes.md).  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Ejemplo ATLDuck](../../top/visual-cpp-samples.md)   
 [CAtlModuleT Class](../../atl/reference/catlmodulet-class.md)   
 [CAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)