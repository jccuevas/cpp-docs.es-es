---
title: Integración de CLR (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740291"
---
# <a name="clr-integration-ccx"></a>Integración de CLR (C++/CX)

Algunos tipos de Windows Runtime reciben un tratamiento C++especial en/CX y los lenguajes basados en el Common Language Runtime (CLR). En este artículo se describe la manera en que varios tipos de un lenguaje se asignan a otro lenguaje. Por ejemplo, CLR asigna Windows.Foundation.IVector to System.Collections.IList, Windows.Foundation.IMap to System.Collections.IDictionary, etc. Del mismo C++modo,/CX asigna de forma especial tipos como platform::D Ombre y Platform:: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Asignación del Windows Runtime a C++/CX

Cuando C++/CX Lee un archivo de metadatos de Windows (. winmd), el compilador asigna automáticamente los tipos C++y espacios de nombres de Windows Runtime comunes a los espacios de nombres y tipos de/CX. Por ejemplo, el tipo `UInt32` de Windows Runtime numérico se asigna automáticamente a. `default::uint32`

C++/CX asigna varios otros tipos de Windows Runtime al espacio de nombres **Platform** . Por ejemplo, el identificador **Windows:: Foundation** HSTRING, que representa una cadena de texto Unicode de solo lectura, se asigna a C++la `Platform::String` clase/CX. Cuando una operación de Windows Runtime devuelve un error HRESULT, se asigna a un C++/CX `Platform::Exception`.

C++/CX también asigna determinados tipos en Windows Runtime espacios de nombres para mejorar la funcionalidad del tipo. Para estos tipos, C++/CX proporciona constructores y métodos auxiliares que son específicos de C++ y no están disponibles en el archivo. winmd estándar del tipo.

En las listas siguientes se muestran estructuras de valor que admiten nuevos métodos del asistente y constructores. Si ha escrito código anteriormente que usa listas de inicialización de estructuras, cámbielo para usar los constructores recién agregados.

**Windows::Foundation**

- Punto

- Rect

- Tamaño

**Windows::UI**

- Color

**Windows::UI::XAML**

- CornerRadius

- Duration

- GridLength

- Thickness

**Windows::UI::XAML::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- Matrix

**Windows::UI::XAML::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Asignación de CLR a C++/CX

Cuando Microsoft C++ o C# los compiladores leen un archivo. winmd, asignan automáticamente determinados tipos del archivo de metadatos a C++los tipos de/CX o CLR adecuados. Por ejemplo, en CLR, la interfaz IVector\<T > está asignada a IList\<T >. Pero en C++/CX, la interfaz\<IVector T > no está asignada a otro tipo.

IReference\<t > en el Windows Runtime se asigna a >\<de t que aceptan valores NULL en .net.

## <a name="see-also"></a>Vea también

[Interoperación con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)
