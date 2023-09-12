using System.Collections;
using System.Collections.Generic;
using Unity.VisualScripting;
using UnityEngine;

public class Enemy_02_Controller : Enemies
{
    [SerializeField] private Transform shotPoint;

    private Rigidbody2D rb2d;

    [SerializeField] private float yMax = 2.5f;
    [SerializeField] private bool canMove;



    // Start is called before the first frame update
    void Start()
    {
        rb2d = GetComponent<Rigidbody2D>();
        rb2d.velocity = new Vector2(0f, -speed);

        waitTime = Random.Range(.5f, 2f);

    }

    // Update is called once per frame
    void Update()
    {
        ShotChase();

        if (transform.position.y < yMax && canMove)
        {
            if (transform.position.x < 0)
            {
                rb2d.velocity = new Vector2(speed, -speed);
                canMove = false;
            }
            else
            { 
                rb2d.velocity = new Vector2(-speed, -speed);
                canMove = false;
            }
           
        }
    }

    private void ShotChase()
    {
        bool visible = GetComponentInChildren<SpriteRenderer>().isVisible;

        if (visible) 
        {
            var player = FindObjectOfType<PlayerController>();

            if (player != null)
            {
                waitTime -= Time.deltaTime;

                if (waitTime <= 0)
                {
                    var shotInst = Instantiate(shot, shotPoint.position, shotPoint.rotation);

                    Vector2 direction = (player.transform.position - shotInst.transform.position).normalized;

                    shotInst.GetComponent<Rigidbody2D>().velocity = direction * shotSpeed;

                    //float angle = Mathf.Atan2(direction.y, direction.x) * Mathf.Rad2Deg;

                    //shotInst.transform.rotation = Quaternion.Euler(0f, 0f, angle);

                    waitTime = Random.Range(1.5f, 2f);
                }
            }

            
        }
    }
}
