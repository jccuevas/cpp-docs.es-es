---
title: "Control de eventos en C++ nativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de eventos, Visual C++"
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de eventos en C++ nativo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el control de eventos de C\+\+ nativo, puede configurar un origen de eventos y un receptor de eventos usando los atributos [event\_source](../windows/event-source.md) y [event\_receiver](../windows/event-receiver.md), respectivamente, que especifican `type`\=`native`.  Estos atributos permiten que las clases a las que se aplican desencadenen controlen eventos en un contexto nativo, no COM.  
  
## Declarar eventos  
 En una clase de origen de eventos, use la palabra clave [\_\_event](../cpp/event.md) en una declaración de método para declarar el método como un evento.  Asegúrese de declarar el método pero no lo defina; si lo hace generará un error del compilador, porque el compilador define el método de manera implícita cuando se convierte en un evento.  Los eventos nativos pueden ser métodos con cero o más parámetros.  El tipo de valor devuelto puede ser void o cualquier tipo entero.  
  
## Definir controladores de eventos  
 En una clase de receptor de eventos, se definen los controladores de eventos, que son métodos con firmas \(tipos de valor devuelto, convenciones de llamada y argumentos\) que coinciden con el evento que van a controlar.  
  
## Enlazar controladores de eventos a eventos  
 También en una clase de receptor de eventos, se usa la función intrínseca [\_\_hook](../cpp/hook.md) para asociar eventos a controladores de eventos y [\_\_unhook](../cpp/unhook.md) para desasociar eventos de los controladores de eventos.  Puede enlazar varios eventos a un controlador de eventos o varios controladores de eventos a un evento.  
  
## Desencadenar eventos  
 Para desencadenar un evento, llame simplemente al método declarado como un evento en la clase del origen de eventos.  Si se han enlazado controladores al evento, se llamará a los controladores.  
  
### Código de evento de C\+\+ nativo  
 En el ejemplo siguiente se muestra cómo activar un evento en C\+\+ nativo.  Para compilar y ejecutar el ejemplo, consulte los comentarios del código.  
  
## Ejemplo  
  
### Código  
  
```  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### Output  
  
```  
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## Vea también  
 [Control de eventos](../cpp/event-handling.md)