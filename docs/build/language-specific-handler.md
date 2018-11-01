---
title: Controlador específico del lenguaje
ms.date: 11/04/2016
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
ms.openlocfilehash: f355c0578cdf898dbe8880b2c839cac5634dcbf4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596337"
---
# <a name="language-specific-handler"></a>Controlador específico del lenguaje

La dirección relativa del controlador específico del lenguaje está presente en UNWIND_INFO cada vez que se establecen marcas UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER. Como se describe en la sección anterior, se denomina controlador específico del lenguaje como parte de la búsqueda de un controlador de excepciones o como parte de una operación de desenredo. Tiene el siguiente prototipo:

```
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** proporciona un puntero a un registro de excepciones, que tiene la definición de Win64 estándar.

**EstablisherFrame** es la dirección de la base de la asignación fija de la pila para esta función.

**ContextRecord** puntos en el contexto de excepción en el momento en que se ha producido la excepción (en el caso del controlador de excepciones) o actual de "desenredo" contexto (en el caso del controlador de terminación).

**DispatcherContext** apunta al contexto del distribuidor para esta función. Tiene la siguiente definición:

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

**ControlPc** es el valor de RIP dentro de esta función. Se trata de una dirección de la excepción o la dirección en la que deja la función establecedora control. Se trata de RIP que se usará para determinar si el control está dentro de algún tipo de construcción protegido dentro de esta función (por ejemplo, un bloque __try para \__try /\__except o \__try /\__finally).

**ImageBase** es la imagen base (dirección de carga) del módulo que contiene esta función, para agregarse a los desplazamientos de 32 bits utilizados en la entrada de la función y la información de desenredo para grabar direcciones relativas.

**FunctionEntry** proporciona un puntero a la RUNTIME_FUNCTION que contiene la función de entrada de función y desenredado direcciones relativas de base de la imagen de información para esta función.

**EstablisherFrame** es la dirección de la base de la asignación fija de la pila para esta función.

**TargetIp** suministra una dirección de instrucción opcional que especifica la dirección de continuación de desenredo. Esta dirección se omite si **EstablisherFrame** no se especifica.

**ContextRecord** apunta al contexto de la excepción, para su uso por el código de envío/desenredo de excepción del sistema.

**LanguageHandler** apunta a la rutina del controlador de lenguaje específico del idioma que se llama.

**HandlerData** apunta a los datos del controlador específicos del lenguaje para esta función.

## <a name="see-also"></a>Vea también

[Control de excepciones (x64)](../build/exception-handling-x64.md)