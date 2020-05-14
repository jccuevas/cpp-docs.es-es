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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493253"
---
# <a name="getprocaddress"></a>GetProcAddress

Los procesos que vinculan explícitamente a un archivo DLL llaman a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función exportada en el archivo DLL. Para llamar a la función DLL, se usa el puntero de función devuelto. **GetProcAddress** toma como parámetros el identificador del módulo DLL (que devuelven **LoadLibrary**, `AfxLoadLibrary` o **GetModuleHandle**) y toma el nombre de la función a la que se quiere llamar o el ordinal de exportación de la función.

Dado que está llamando a la función DLL a través de un puntero y no hay ninguna comprobación de tipos en tiempo de compilación, asegúrese de que los parámetros de la función sean correctos, para no sobrepasar la memoria asignada en la pila y provocar una infracción de acceso. Una manera de ayudar a proporcionar seguridad de tipos consiste en examinar los prototipos de función de las funciones exportadas y crear definiciones de tipo coincidentes para los punteros de función. Por ejemplo:

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

La forma en que se especifica la función que se quiere usar al llamar a **GetProcAddress** depende de cómo se compiló el archivo DLL.

Solo se puede obtener el ordinal de exportación si el archivo DLL al que se está vinculando está compilado con un archivo de definición de módulo (.def) y si los ordinales están enumerados con las funciones de la sección **EXPORTS** del archivo .def del archivo DLL. El proceso de llamar a **GetProcAddress** con un ordinal de exportación, en vez de con el nombre de función, es ligeramente más rápido si el archivo DLL tiene muchas funciones exportadas, ya que los ordinales de exportación sirven como índices en la tabla de exportación del archivo DLL. Con un ordinal de exportación, **GetProcAddress** puede ubicar la función directamente, en lugar de comparar el nombre especificado con los nombres de función que figuran en la tabla de exportación del archivo DLL. Aun así, debe llamar a **GetProcAddress** con un ordinal de exportación únicamente si controla la asignación de los ordinales a las funciones exportadas en el archivo .def.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportación desde un archivo DLL mediante archivos DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
