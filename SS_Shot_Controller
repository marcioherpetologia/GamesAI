using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ShotController : MonoBehaviour
{
    private Rigidbody2D rb2d;
    [SerializeField] private float speed;

    [SerializeField] private GameObject shotImpact;

    // Start is called before the first frame update
    void Start()
    {
        rb2d = GetComponent<Rigidbody2D>();
        //rb2d.velocity = new Vector2(0f, speed);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Enemy"))
        {
            other.GetComponent<Enemies>().EnemyDamage(1);           
        }

        if (other.CompareTag("Player"))
        { 
            other.GetComponent<PlayerController>().PlayerDamage(1);
        }

        Destroy(gameObject);
        Instantiate(shotImpact, transform.position, transform.rotation);
    }
}
