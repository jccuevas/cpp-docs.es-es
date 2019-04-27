---
title: Procedimiento Crear y usar instancias de CComPtr y CComQIPtr
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 2bcabfe80185939b899c84fc44f71b98608fc3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154066"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Procedimiento Crear y usar instancias de CComPtr y CComQIPtr

En la programación clásica de Windows, a menudo las bibliotecas se implementan como objetos COM (o más concretamente, como servidores COM). Muchos componentes del sistema operativo Windows se implementan como servidores COM y muchos colaboradores proporcionan bibliotecas en este formato. Para obtener información sobre los conceptos básicos de COM, vea [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal).

Cuando cree instancias de un objeto del Modelo de objetos componentes (COM), almacena el puntero de interfaz en un puntero inteligente COM, que realiza el recuento de referencias mediante llamadas a `AddRef` y `Release` en el destructor. Si usa Active Template Library (ATL) o la biblioteca MFC (Microsoft Foundation Class), use el puntero inteligente de `CComPtr` . Si no usa ATL o MFC, use `_com_ptr_t`. Como no existe un equivalente COM para `std::unique_ptr`, use estos punteros inteligentes para los escenarios de un solo propietario y de varios propietarios. `CComPtr` y `ComQIPtr` admiten las operaciones de movimiento que tienen referencias rvalue.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar `CComPtr` para crear una instancia de un objeto COM y obtener punteros a sus interfaces. Observe que la función miembro `CComPtr::CoCreateInstance` se usa para crear el objeto COM, en lugar de la función Win32 que tiene el mismo nombre.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` y sus relativos forman parte de la biblioteca ATL y se definen en \<atlcomcli.h >. `_com_ptr_t` se declara en \<comip.h >. El compilador crea especializaciones de `_com_ptr_t` cuando genera clases contenedoras para bibliotecas de tipos.

## <a name="example"></a>Ejemplo

ATL también proporciona `CComQIPtr`, que tiene una sintaxis más sencilla para consultar un objeto COM para recuperar una interfaz adicional. Sin embargo, se recomienda `CComPtr` porque hace todo lo que `CComQIPtr` puede hacer y es semánticamente más coherente con los punteros de interfaz COM sin formato. Si usa un `CComPtr` para consultar una interfaz, el nuevo puntero de interfaz se coloca en un parámetro de salida. Si se produce un error en la llamada, se devuelve un valor HRESULT, que es el patrón COM típico. Con `CComQIPtr`, el valor devuelto es el propio puntero y, si se produce un error en la llamada, no se puede tener acceso al valor devuelto HRESULT interno. Las dos líneas siguientes muestran cómo los mecanismos de control de errores en `CComPtr` y `CComQIPtr` son diferentes.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Ejemplo

`CComPtr` proporciona una especialización para IDispatch que le permite almacenar punteros en los componentes de automatización COM e invocar los métodos de la interfaz mediante un enlace en tiempo de ejecución. `CComDispatchDriver` es un typedef para `CComQIPtr<IDispatch, &IIDIDispatch>`, que es implícitamente convertible a `CComPtr<IDispatch>`. Por lo tanto, cuando cualquiera de estos tres nombres aparece en el código, es equivalente a `CComPtr<IDispatch>`. En el ejemplo siguiente se muestra cómo obtener un puntero para el modelo de objetos de Microsoft Word mediante un `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Vea también

[Punteros inteligentes (C++ moderno)](../cpp/smart-pointers-modern-cpp.md)
