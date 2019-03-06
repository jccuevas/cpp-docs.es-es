---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: e20c9ad913744879dcc15a9b4c177799cc59f654
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421342"
---
# <a name="getprocaddress"></a>GetProcAddress

Los procesos que se vinculan explícitamente a una llamada DLL [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función exportada en el archivo DLL. Use el puntero de función devuelto para llamar a la función DLL. **GetProcAddress** toma como parámetros el identificador de módulo del archivo DLL (devuelto por **LoadLibrary**, `AfxLoadLibrary`, o **GetModuleHandle**) y toma el nombre de la función que desee se debe llamar o el ordinal de exportación de la función.

Dado que está llamando a la función DLL mediante un puntero y no hay ninguna comprobación de tipo en tiempo de compilación, asegúrese de que los parámetros a la función son correctos para que no sobrepasar la memoria asignada en la pila y provocar una infracción de acceso. Una manera de ayudar a proporcionar seguridad de tipos es consultar los prototipos de función de las funciones exportadas y crear definiciones typedef coincidentes para los punteros de función. Por ejemplo:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

Cómo especificar la función que desee al llamar a **GetProcAddress** depende de cómo se creó el archivo DLL.

Solo puede obtener el ordinal de exportación si se compila el archivo DLL se vincula a con un archivo de módulo (.def) de la definición y si los ordinales figuran en las funciones de la **exportaciones** sección del archivo .def de la DLL. Una llamada a **GetProcAddress** con una exportación ordinal en lugar del nombre de función es ligeramente más rápido si el archivo DLL tiene muchas funciones exportadas, dado que los ordinales exportados sirven como índices en la DLL exportación la tabla. Con un ordinal de exportación, **GetProcAddress** puede encontrar la función directamente en lugar de comparar el nombre especificado con los nombres de función en la tabla de exportación del archivo DLL. Sin embargo, debe llamar a **GetProcAddress** con un ordinal de exportación solo si tiene control sobre la asignación de ordinales a las funciones exportadas en el archivo. def.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportación desde un archivo DLL mediante archivos DEF](../build/exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)
