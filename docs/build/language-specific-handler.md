---
title: "Controlador espec&#237;fico del lenguaje | Microsoft Docs"
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
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Controlador espec&#237;fico del lenguaje
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La dirección relativa del controlador específico del lenguaje está presente en UNWIND\_INFO cada vez que se establecen marcadores UNW\_FLAG\_EHANDLER o UNW\_FLAG\_UHANDLER.  Como se describió en la sección anterior, se efectúa una llamada al controlador específico del lenguaje como parte del proceso de búsqueda de un controlador de excepciones o como parte de una operación de desenredo.  Tiene el siguiente prototipo:  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **ExceptionRecord** proporciona un puntero a un registro de excepciones, que tiene la definición de Win64 estándar.  
  
 **EstablisherFrame** es la dirección de la base de la asignación del espacio fijo de la pila correspondiente a esta función.  
  
 **ContextRecord** señala al contexto de la excepción en el instante en que ésta se originó \(en el caso del controlador de excepciones\) o el contexto de "desenredo" actual \(en el caso del controlador de terminación\).  
  
 **DispatcherContext** señala al contexto del distribuidor para esta función.  Tiene la siguiente definición:  
  
```  
typedef struct _DISPATCHER_CONTEXT {  
    ULONG64 ControlPc;  
    ULONG64 ImageBase;  
    PRUNTIME_FUNCTION FunctionEntry;  
    ULONG64 EstablisherFrame;  
    ULONG64 TargetIp;  
    PCONTEXT ContextRecord;  
    PEXCEPTION_ROUTINE LanguageHandler;  
    PVOID HandlerData;  
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;  
```  
  
 **ControlPc** es el valor de RIP dentro de esta función.  Puede ser una dirección de una excepción o la dirección en la que el control salió de la función establecedora.  Este es el valor de RIP que se utilizará para determinar si el control está dentro de alguna construcción protegida incluida en esta función \(por ejemplo, un bloque \_\_try para \_\_try\/\_\_except o \_\_try\/\_\_finally\).  
  
 **ImageBase** es la imagen base \(dirección de carga\) del módulo que contiene esta función, para agregarse a los desplazamientos de 32 bits empleados en la entrada de la función e información de desenredo para registrar direcciones relativas.  
  
 **FunctionEntry** proporciona un puntero a la entrada de función RUNTIME\_FUNCTION que contiene la función y direcciones de información de desenredo relativas a la imagen base para esta función.  
  
 **EstablisherFrame** es la dirección de la base de la asignación del espacio fijo de la pila correspondiente a esta función.  
  
 **TargetIp** Proporciona una dirección de instrucción opcional que especifica la dirección de continuación del desenredo.  Esta dirección se omite si no se especifica **EstablisherFrame**.  
  
 **ContextRecord** señala al contexto de la excepción, para uso por parte del código de distribución\/desenredo de excepciones del sistema.  
  
 **LanguageHandler** señala a la rutina del controlador de lenguaje específica del lenguaje a la que se llama.  
  
 **HandlerData** señala a los datos del controlador específicos del lenguaje para esta función.  
  
## Vea también  
 [Control de excepciones \(x64\)](../build/exception-handling-x64.md)