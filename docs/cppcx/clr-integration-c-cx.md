---
title: Integración de CLR (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95dd817e7081eea6371e9dab9d95aec06d22971c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110771"
---
# <a name="clr-integration-ccx"></a>Integración de CLR (C++/CX)

Algunos tipos de Windows en tiempo de ejecución reciben un tratamiento especial en C / c++ / CX y los idiomas que se basan en common language runtime (CLR). En este artículo se describe la manera en que varios tipos de un lenguaje se asignan a otro lenguaje. Por ejemplo, CLR asigna Windows.Foundation.IVector to System.Collections.IList, Windows.Foundation.IMap to System.Collections.IDictionary, etc. De forma similar, C++ / c++ / CX asigna especialmente tipos como Platform:: Delegate y Platform:: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Asignar el tiempo de ejecución de Windows en C++ / c++ / CX

Cuando C++ / c++ / CX lee un archivo de metadatos (.winmd) de Windows, el compilador asigna automáticamente espacios de nombres comunes de Windows Runtime y tipos de C / c++ / CX espacios de nombres y tipos. Por ejemplo, el tipo en tiempo de ejecución de Windows numérico `UInt32` se asignan automáticamente a `default::uint32`.

C++ / c++ / CX asigna varios otros tipos en tiempo de ejecución de Windows para el **plataforma** espacio de nombres. Por ejemplo, el **Windows::Foundation** identificador HSTRING, que representa una cadena de texto Unicode de solo lectura, se asigna a C++ / c++ / CX `Platform::String` clase. Cuando una operación de Windows Runtime devuelve un HRESULT de error, se asigna a C++ / c++ / CX `Platform::Exception`.

C++ / c++ / CX también asigna determinados tipos en espacios de nombres en tiempo de ejecución de Windows para mejorar la funcionalidad del tipo. Para estos tipos, C / c++ / CX proporciona constructores auxiliares y métodos que son específicas de C++ y no están disponibles en el archivo de .winmd estándar del tipo.

En las listas siguientes se muestran estructuras de valor que admiten nuevos métodos auxiliares y constructores. Si ha escrito código anteriormente que usa listas de inicialización de estructuras, cámbielo para usar los constructores recién agregados.

**Windows::Foundation**

- Punto

- Rect

- Tamaño

**Windows::UI**

- Color

**Windows::UI::XAML**

- CornerRadius

- Duración

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

## <a name="mapping-the-clr-to-ccx"></a>Asignación de CLR a C++ / c++ / CX

Cuando los compiladores de C# o Visual C++ leen un archivo .winmd, asignan automáticamente determinados tipos en el archivo de metadatos adecuado C++ / c++ / CX o CLR de tipos. Por ejemplo, en el CLR, el IVector\<T > interfaz se asigna a IList\<T >. Pero en C / c++ / CX, el IVector\<T > interfaz no está asignada a otro tipo.

IReference\<T > en el tiempo de ejecución de Windows se asigna a Nullable\<T > en. NET.

## <a name="see-also"></a>Vea también

[Interoperar con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)