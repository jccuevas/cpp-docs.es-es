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
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493253"
---
# <a name="getprocaddress"></a>GetProcAddress

Los procesos que se vinculan explícitamente a un archivo DLL llaman a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función exportada en el archivo dll. El puntero de función devuelto se usa para llamar a la función DLL. **GetProcAddress** toma como parámetros el identificador del módulo DLL (devueltopor LoadLibrary `AfxLoadLibrary`, o **GetModuleHandle**) y toma el nombre de la función a la que desea llamar o el ordinal de exportación de la función.

Dado que está llamando a la función DLL a través de un puntero y no hay ninguna comprobación de tipos en tiempo de compilación, asegúrese de que los parámetros de la función son correctos para que no se pase por alta la memoria asignada en la pila y se produzca una infracción de acceso. Una manera de ayudar a proporcionar seguridad de tipos es examinar los prototipos de función de las funciones exportadas y crear definiciones typedef coincidentes para los punteros de función. Por ejemplo:

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

La forma de especificar la función que desea al llamar a **GetProcAddress** depende de cómo se compiló el archivo dll.

Solo se puede obtener el ordinal de exportación si el archivo DLL al que se está vinculando se crea con un archivo de definición de módulo (. def) y si los ordinales se enumeran con las funciones de la sección Exports del archivo. def del archivo dll. Llamar a **GetProcAddress** con un ordinal de exportación, en oposición al nombre de función, es ligeramente más rápido si el archivo dll tiene muchas funciones exportadas, ya que los ordinales de exportación sirven como índices en la tabla de exportación del archivo dll. Con un ordinal de exportación, **GetProcAddress** puede localizar la función directamente en lugar de comparar el nombre especificado con los nombres de función de la tabla de exportación del archivo dll. Sin embargo, debe llamar a **GetProcAddress** con un ordinal de exportación solo si tiene el control sobre la asignación de los ordinales a las funciones exportadas en el archivo. def.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportación desde un archivo DLL mediante archivos DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
