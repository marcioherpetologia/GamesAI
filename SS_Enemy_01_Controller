using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Enemy_01_Controller : Enemies
{
    private Rigidbody2D rb2d;

    [Header("Shot Variables")]    
    [SerializeField] private Transform firePoint;
    

    // Start is called before the first frame update
    void Start()
    {
        rb2d = GetComponent<Rigidbody2D>();
        rb2d.velocity = new Vector2(0f, -speed);

        waitTime = Random.Range(0.5f, 2f);
    }

    // Update is called once per frame
    void Update()
    {
        Shot();
    }

    private void Shot()
    {
        bool visible = GetComponentInChildren<SpriteRenderer>().isVisible;

        if (visible)
        {
            waitTime -= Time.deltaTime;

            if (waitTime <= 0)
            {
                var shotInst = Instantiate(shot, firePoint.position, firePoint.rotation);
                shotInst.GetComponent<Rigidbody2D>().velocity = new Vector2(0f, -shotSpeed);

                waitTime = Random.Range(1.5f, 2f);
            }

        }
    }
}
    
