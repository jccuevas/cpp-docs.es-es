---
title: Importar a una aplicación mediante __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440413"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>Importar a una aplicación mediante __declspec(dllimport)

Se dice que un programa que utiliza símbolos públicos definidos por un archivo DLL importa dichos símbolos. Cuando cree archivos de encabezado para aplicaciones en las que se usan los archivos DLL para la compilación, utilice **__declspec(dllimport)** en las declaraciones de los símbolos públicos. La palabra clave **__declspec(dllimport)** funciona tanto si exporta con archivos .def como con la palabra clave **__declspec(dllexport)** .

Para que el código sea más legible, defina una macro para **__declspec(dllimport)** y después úsela para declarar cada símbolo importado:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

El uso de **__declspec(dllimport)** es opcional en las declaraciones de función, pero el compilador genera un código más eficaz si usa esta palabra clave. Pero debe usar **__declspec(dllimport)** para que el ejecutable importador pueda acceder a los símbolos y objetos de datos públicos del archivo DLL. Tenga en cuenta que los usuarios del archivo DLL aún deben vincularse a una biblioteca de importación.

Puede utilizar el mismo archivo de encabezado para el archivo DLL y para la aplicación de cliente. Para ello, utilice un símbolo de preprocesador especial que indique si está compilando el archivo DLL o la aplicación de cliente. Por ejemplo:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicialización de un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Vea también

[Importación a una aplicación](importing-into-an-application.md)
