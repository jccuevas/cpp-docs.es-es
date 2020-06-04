---
title: Error de las herramientas del vinculador LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: bedf96262944d59737a39a942021cdec9445f3b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990951"
---
# <a name="linker-tools-error-lnk1256"></a>Error de las herramientas del vinculador LNK1256

Error de operación ALINK: razón

Una razón común para LNK1256 es un número de versión incorrecto para un ensamblado. El valor 65535 no está permitido en ninguna parte del número de versión del ensamblado. El intervalo válido para las versiones de ensamblado es 0-65534.

LNK1256 también puede producirse si ALINK no pudo encontrar el contenedor de claves nombrado. Elimine el contenedor de claves y agréguelo de nuevo al CSP de nombre seguro mediante [SN. exe (herramienta de nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Otra razón para el error LNK1256 es una discrepancia de versiones entre el vinculador y Alink.dll. Esto puede deberse a una instalación dañada de Visual Studio. Use **programas y características** en el panel de control de Windows para reparar o reinstalar Visual Studio.

En el siguiente ejemplo se genera el error LNK1256:

```cpp
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```
