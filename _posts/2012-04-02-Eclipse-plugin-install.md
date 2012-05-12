---
layout: post
title: Eclipse 插件安装
description: 工具代码
categories:
- java
tags:
- Eclipse
---

之前通过Links安装在较新的版本不太好使
后来的eclipse(myeclipse)可以通过把插件目录扔到dropins里自动安装

我选择直接往bundles.info加插件地址

<pre class="prettyprint">
public class CreatePluginsConfig {
	public static void print(String path) {
		List list = getFileList(path);
		if (list == null) {
			return;
		}

		int length = list.size();
		for (int i = 0; i < length; i++) {
			String result = "";
			String thePath = String.valueOf(list.get(i));
			File file = new File(thePath);
			if (file.isDirectory()) {
				String fileName = file.getName();
				if (fileName.indexOf("_") < 0) {

					print(thePath);
					continue;
				}
				String[] filenames = fileName.split("_");
				String filename1 = filenames[0];
				String filename2 = filenames[1];
				result = filename1 + "," + filename2 + ",file:/" + path + "/"
						+ fileName + "/,4,false";
				result = getFormatPath(result);
				System.out.println(result);

			} else if (file.isFile()) {
				String fileName = file.getName();
				if (fileName.indexOf("_") < 0) {
					continue;
				}
				int last = fileName.lastIndexOf("_");
				String filename1 = fileName.substring(0, last);
				String filename2 = fileName.substring(last + 1,
						fileName.length() - 4);
				result = filename1 + "," + filename2 + ",file:/" + path + "/"
						+ fileName + ",4,false";
				result = getFormatPath(result);
				System.out.println(result);
			}
		}
	}

	public static List getFileList(String path) {
		path = path + "/";
		File filePath = new File(path);
		if (!filePath.isDirectory()) {
			return null;
		}
		String[] filelist = filePath.list();
		List filelistFilter = new ArrayList();

		for (int i = 0; i < filelist.length; i++) {
			String tempfilename = path + filelist[i];
			filelistFilter.add(tempfilename);
		}
		return filelistFilter;
	}

	public static void printAllPlugins(String path) {
		File files[] = new File(path).listFiles();
		for (File file : files) {
			System.out.println("#" + file.getName());
			print(file.getAbsolutePath());
			System.out.println();
		}
	}

	public static String getFormatPath(String path) {
		path = path.replaceAll("\\\\", "/");
		return path;
	}

	public static void main(String[] args) {
		String path = "d:/dev/java/EclipsePlugin";
		printAllPlugins(path);
	}
}


</pre>

<pre class="prettyprint">
#fullscreen
cn.pande.eclipsex.fullscreen,1.0.7,file:/d:/dev/java/EclipsePlugin/fullscreen/cn.pande.eclipsex.fullscreen_1.0.7.jar,4,false

#git
org.eclipse.egit.core,1.3.0.201202151440-r,file:/d:/dev/java/EclipsePlugin/git/org.eclipse.egit.core_1.3.0.201202151440-r.jar,4,false
.....


</pre>

另外我对整个eclipse安装目录用git管理了

