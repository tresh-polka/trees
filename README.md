# trees

Пример:

import {
    mkfile, mkdir, isDirectory, isFile, map,
  } from '@hexlet/immutable-fs-trees';
  
  isFile(mkfile('config')); // true
  isDirectory(mkdir('etc')); // true
  
  const tree = mkdir('etc', [mkfile('config'), mkfile('hosts')]);
  
  const callbackFn = (node) => {
    const { name } = node;
    const newName = name.toUpperCase();
    return { ...node, name: newName };
  };
  
  map(callbackFn, tree);
  // {
  //   name: 'ETC',
  //   children: [
  //     { name: 'CONFIG', meta: {}, type: 'file' },
  //     { name: 'HOSTS', meta: {}, type: 'file' }
  //   ],
  //   meta: {},
  //   type: 'directory',
  // }
  