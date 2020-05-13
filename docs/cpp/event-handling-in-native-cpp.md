---
title: Control de eventos en C++ nativo
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: cc9265cd3f9f400e2880405019e4d2c9a934f10a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180087"
---
# <a name="event-handling-in-native-c"></a>Control de eventos en C++ nativo

En el C++ control de eventos nativo, se configura un origen de eventos y un receptor de eventos mediante los atributos [event_source](../windows/attributes/event-source.md) y [event_receiver](../windows/attributes/event-receiver.md) , respectivamente, que especifican `type`=`native`. Estos atributos permiten que las clases a las que se aplican desencadenen controlen eventos en un contexto nativo, no COM.

## <a name="declaring-events"></a>Declarar eventos

En una clase de origen de eventos, use la palabra clave [__event](../cpp/event.md) en una declaración de método para declarar el método como un evento. Asegúrese de declarar el método pero no lo defina; si lo hace generará un error del compilador, porque el compilador define el método de manera implícita cuando se convierte en un evento. Los eventos nativos pueden ser métodos con cero o más parámetros. El tipo de valor devuelto puede ser void o cualquier tipo entero.

## <a name="defining-event-handlers"></a>Definir controladores de eventos

En una clase de receptor de eventos, se definen los controladores de eventos, que son métodos con firmas (tipos de valor devuelto, convenciones de llamada y argumentos) que coinciden con el evento que van a controlar.

## <a name="hooking-event-handlers-to-events"></a>Enlazar controladores de eventos a eventos

Además, en una clase de receptor de eventos, se usa la función intrínseca [__hook](../cpp/hook.md) para asociar eventos a controladores de eventos y [__unhook](../cpp/unhook.md) para desasociar eventos de los controladores de eventos. Puede enlazar varios eventos a un controlador de eventos o varios controladores de eventos a un evento.

## <a name="firing-events"></a>Desencadenar eventos

Para desencadenar un evento, llame simplemente al método declarado como un evento en la clase del origen de eventos. Si se han enlazado controladores al evento, se llamará a los controladores.

### <a name="native-c-event-code"></a>Código de evento de C++ nativo

En el ejemplo siguiente se muestra cómo activar un evento en C++ nativo. Para compilar y ejecutar el ejemplo, consulte los comentarios del código.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
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

### <a name="output"></a>Output

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Consulte también

[Control de eventos](../cpp/event-handling.md)
