package com.Trie;

public class Trie {
    class Node
    {
        boolean flag;
        Node[] table = new Node[26];
        Node()
        {
            flag=false;
            for(int i=0;i<table.length;i++)
            {
                table[i]=null;
            }
        }
    }

    private Node head;
    Trie()
    {
        this.head=new Node();
    }
    public void insert(String s)
    {
        Node pointer = this.head;
        for(int i=0;i<s.length();i++)
        {    char c = s.charAt(i);
            if(pointer.table[c-'a']==null)
                pointer.table[c-'a']=new Node();

            pointer=pointer.table[c-'a'];
        }
        pointer.flag=true;
    }

    public boolean search(String s)
    {   Node pointer = this.head;
        for(int i=0;i<s.length();i++)
        {
            char c = s.charAt(i);
            if(pointer.table[c-'a']==null)
                return false;

            pointer=pointer.table[c-'a'];
        }
        return pointer.flag;
    }
}
